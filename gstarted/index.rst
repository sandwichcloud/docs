Getting Started
===============

Requirements
------------

VCenter 6.5
^^^^^^^^^^^

You must have a ready to use VCenter server with the following resources:

* At least one Datastore
* At least one VM Compute Cluster
* At least one Host
* At least one non-management Port Group

The firewall on all hosts (within a cluster) that will be added to Sandwich Cloud
needs to allow outgoing connections on the "VM serial port connected to vSPC" service.

All hosts **MUST** be able to connect to your workstation on port 13370. This is used
for the Sandwich Cloud Metadata Service. Without this instances will not be able
to get networking configuration.

Networking
^^^^^^^^^^

The mentioned Port Group in the VCenter requirements must be connected to a
layer 3 network that is reachable from your workstation. It is recommended
that no other devices be on this network aside from a router to prevent possible
IP address overlaps.

Workstation
^^^^^^^^^^^

* Internet Access
* Docker
    * If you are not using Docker for Mac or Docker for Windows the steps in
      "Setting up the CLI" may need to be modified to fit your environment.

Setting up the Environment
--------------------------

For this guide we will be using the Sandwich Cloud quick-start repository that
will spin up Sandwich Cloud containers and it's dependencies using docker-compose.

So let's start by cloning the repository and changing our working directory to it.

.. code::

   git clone https://github.com/sandwichcloud/quick-start.git
   cd quick-start

Configuration
^^^^^^^^^^^^^

Most of the configuration items are already set however we still need to configure
a few things.

First copy the :code:`.env-sample` file to :code:`.env`

.. code::

   cp .env-sample .env

Under the :code:`VCENTER` heading enter your connection parameters used to
onnect to your VCenter server. It is recommended to use a user that has admin
privileges, however any user with the correct permissions will work.


.. code::

   VCENTER_HOST=vcenter.exmple.com
   VCENTER_PORT=443
   VCENTER_USERNAME=administrator@vsphere.local
   VCENTER_PASSWORD=password123

You also must give the :code:`MENU_URL`. This is the telnet url to the metadata
service for Sandwich Cloud. The host in this url should be your workstation's
address and must be reachable by your compute hosts. The metadata service's port
is set to 13370 and must be given in the url.

.. code::

   MENU_URL=telnet://192.168.0.32:13370

Launching
^^^^^^^^^

Now that everything is configured we can go ahead and launch all the services.

.. code::

  docker-compose up

You must wait until all services are started before continuing. You will see the
following output when everything is done launching:

.. code::

   deli-manager_1             | [2018-01-11T01:20:58+0000][deli.manager.cli.commands.run.RunManager][INFO] Creating CRDs
   deli-menu_1                | [2018-01-11T01:20:58+0000][deli.menu.vspc.server.VSPCServer][INFO] Serving on ('0.0.0.0', 13370)
   deli-manager_1             | [2018-01-11T01:21:08+0000][deli.manager.cli.commands.run.RunManager][INFO] CRDs have been created

Create the database
^^^^^^^^^^^^^^^^^^^

The quick-start is configured to use Database Auth so you must run the database
migrations.

.. code::

   docker-compose exec deli-counter deli_counter database upgrade

Creating the admin user
^^^^^^^^^^^^^^^^^^^^^^^

The admin user is not created by default so we must create it and generate a
password.

You can do that by running the following command:

.. code::

   docker-compose exec deli-counter deli_counter database gen-admin

**Make a note of the password as it will be used later.**

First Steps
-----------

Setting up the CLI
^^^^^^^^^^^^^^^^^^

To get started you first need to download the CLI. Download the latest release
of the CLI from https://github.com/sandwichcloud/deli-cli/releases.

Once the CLI is downloaded you need to configure it to connect to the api server:

.. code::

   export DLEI_API_SERVER=http://localhost:8080

Now you can login to the API:

.. code::

   deli auth login -u admin

When prompted enter the password for the generated admin user. Once verified an
API token will be generated and saved in :code:`~/.sandwich/credentials`. This
API token will automatically be used by the CLI to authenticate against the API.

Creating a Region
^^^^^^^^^^^^^^^^^

In Sandwich Cloud, a Region is linked to a VCenter Datacenter as well as an
Image Datastore.

The Image Datastore is just a VCenter Datastore that we designate as our Image
storage. This Datastore must be connected to all VCenter Compute Clusters that
you want to make available to Sandwich Cloud.

You can create a region by running the following:

.. code::

   deli region create --datacenter ${DATACENTER_NAME} --image-datastore ${DATASTORE_NAME} region1

**Make a note of the region id as this will be used later.**

Now that we have a region we need to enable scheduling to it. If we don't VMs cannot
be launched in this region.

.. code::

  deli region update --schedulable ${REGION_ID}

Creating a Network
^^^^^^^^^^^^^^^^^^

Networks are unique to Regions and require a VCenter Port Group. This Port Group
must be connected to all VCenter Compute Clusters that you want to make available.

You also must already have a routable address space available for that Port
Group. It is recommended that there are no other devices other than a router
present on this address space.

To get started please have handy the CIDR and the default gateway for the
address space. You also must decide on an address pool within the CIDR. This
typically ranges from the first usable address to the last usable address, the
gateway will be automatically excluded from this range.

We will be using Google's DNS servers to make things simple, however feel free
to substitute your own. At least one DNS server must be given.

Once you have those run the following command:

.. code::

   deli network create --port-group ${PORT_GROUP} --region-id ${REGION_ID} \
   --cidr ${CIDR} --gateway ${GATEWAY} --dns-server 8.8.8.8 --dns-server 8.8.4.4 \
   --pool-start ${POOL_START} --pool-end ${POOL_END} my-network

**Make a note of the network id as this will be used later.**

Creating a Zone
^^^^^^^^^^^^^^^

Zones, unique to Regions, are linked to VCenter Compute Clusters. They also,
similar to regions, require their own Datastore that we call the VM Datastore.
The VM Datastore must be shared across all Hosts within the VM Compute Cluster
and will store all active VMs and Volumes within the Zone.

To create a zone run the following:

.. code::

   deli zone create --region-id ${REGION_ID} --vm-cluster ${VM_COMPUTE_CLUSTER} \
   --vm-datastore ${VM_DATASTORE} region1-a

Creating a Project
^^^^^^^^^^^^^^^^^^

Now that we have added compute resources we can logically separate these resources
into Projects. Projects can be specific to applications, teams, or departments,
it is really up to you.

.. code::

   deli project create my-project

Now that you have your project you must configure your CLI to be scoped to that
Project.

.. code::

   deli auth scope ${PROJECT_ID}

Scoping to a project simply takes your auth token and generates a new one that has
permissions to modify resources within the Project. However don't worry, your
original token is still available and can still be used to interact with
non-project based resources as well as scoping to other Projects.

By default projects are not allowed to create any resources, you can fix this
by modifying the quota for the project.

.. code::

   deli project quota modify --vcpu=12 --ram=8182 --disk=100

If you don't care about quota you can set vcpu, ram, and disk to -1 and the
project will be able to use unlimited resources. However, setting project quotas
is recommended as it is a good way to limit resource usage in your Datacenter.

Importing an Image
^^^^^^^^^^^^^^^^^^

Before we launch an instance we first must have an Image to launch from.

An Image is simply a VM Template with a preinstalled OS configured in a certain
way to be compatible with Sandwich Cloud.

Official Images can be downloaded from https://github.com/sandwichcloud/images/releases.
If you do not wish to download a pre-build image feel free to build one yourself by using
the packer scripts in https://github.com/sandwichcloud/images.

Once the Image is downloaded, un-compress it, upload it into the Image Datastore
and create a VM with the only hard drive set to the downloaded VMDK. The VM should
have the following hardware:

* 1 CPU
* 512MB Memory
* 1 Hard Disk (set to the downloaded vmdk)
* 1 SCSI Controller (set to VMware Paravirtual)
* 1 Network adapter

**Do not add any other hardware to the VM as it may create issues with operation.**

Do not boot up the VM as it will introduce unwanted log files into the image.
Make sure the image is placed inside the Datacenter and Image Datastore you
specified when you created the region.

Once the image is imported to VCenter convert it to a template then you can
import it to Sandwich Cloud.

.. code::

   deli image import --region-id ${REGION_ID} my-new-image $TEMPLATE_NAME

**Make a note of the image id as this will be used later.**

.. note::

   To read more about images and learn how to create your own see: :doc:`../admin/images`

Creating a Flavor
^^^^^^^^^^^^^^^^^

Flavors define instances types or sizing of instances. Flavors control the vcpus,
ram, and root disk size of instances.

By default there are no flavors defined so you must create one.

.. code::

   deli flavor create --vcpus 2 --ram 2048 --disk 20 my-flavor

**Make a note of the flavor id as this will be used later.**

Creating a SSH Keypair
^^^^^^^^^^^^^^^^^^^^^^

You are almost ready to launch an instance but we are missing one piece, an SSH
key. For this guide we will be generating a new SSH key, however feel free to use
the :code:`import` command to import your own.

.. code::

   deli keypair generate my-keypair

**Make a note of the keypair id as this will be used later.**

Launching an Instance
^^^^^^^^^^^^^^^^^^^^^

Now you can finally launch the instance!

.. code::

   deli instance create --region-id ${REGION_ID} --network-id ${NETWORK_ID} \
   --flavor-id ${FLAVOR_ID} --image-id ${IMAGE_ID} --keypair-id ${KEYPAIR_ID} my-instance

The instance will now be launching in VCenter. You can get the state of the
instance by running the following command:

.. code::

   deli instance inspect ${INSTANCE_ID}

Once the instance state has changed to 'Created' it has now booted. To get the IP
address of the instance inspect the instance and find the :code:`network_port_id`,
then inspect the network port to grab it's IP address:

.. code::

   deli network port inspect ${NETWORK_PORT_ID}

Now you can SSH into the instance!

.. code::

   ssh cloud-user@${IP_ADDRESS} -i ~/.ssh/id_my-keypair
