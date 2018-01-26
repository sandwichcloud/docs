instance
========

instance create
---------------

Create an instance

.. code::

   deli instance create
     --region-id <region-id>
     --zone-id <zone-id>
     --image-id <image-id>
     --service-account-id <service-account-id>
     --network-id <network-id>
     --flavor-id <flavor-id>
     --disk <size>
     --keypair-id <keypair-id>
     --tag <key>=<value>
     <name>

:code:`--region-id <region-id>`
  The region to launch the instance in

:code:`--zone-id <zone-id>`
  Optional. The zone to launch the instance in

:code:`--image-id <image-id>`
  The image to launch the instance from

:code:`--service-account-id <service-account-id>`
     Optional. The service account to attach to the instance

:code:`--network-id <network-id>`
  The network to attach the instance to

:code:`--flavor-id <flavor-id>`
  The flavor of the instance to launch

:code:`--disk <size>`
  Optional. The size of the root disk to create, this overrides the flavor

:code:`--keypair-id <keypair-id>`
  Optional. A keypair to add to the instance. Can be set multiple times for multiple
  keypairs

:code:`--tag <key>=<value>`
  Optional. A metadata tag to add to the instance. Can be set multiple times for
  multiple tags

instance delete
---------------

Delete an instance

.. code::

   deli instance delete <instance-id>

:code:`<instance-id>`
  The instance ID

instance inspect
----------------

Inspect an instance

.. code::

   deli instance inspect <instance-id>

:code:`<instance-id>`
  The instance ID

instance list
-------------

List instances

.. code::

   deli instance list
     --image-id <image-id>

:code:`--image-id <image-id>`
  Optional. The image ID to filter instances by

instance image
--------------

Create an image from an instance

.. code::

   deli instance image
     --name <name>
     <instance-id>

:code:`--name <name>`
  The image name

:code:`<instance-id>`
  The instance ID

instance restart
----------------

Restart an instance

.. code::

   deli instance restart
     --hard
     --timeout <timeout>
     <instance-id>

:code:`--hard`
  Optional. Hard stop the instance

:code:`--timeout <timeout>`
  Optional. Time in seconds until the instance is hard stopped. Default: 60

:code:`<instance-id>`
  The instance ID

instance start
--------------

Start an instance

.. code::

   deli instance start <instance-id>

:code:`<instance-id>`
  The instance ID

instance stop
-------------

Stop an instance

.. code::

   deli instance restart
     --hard
     --timeout <timeout>
     <instance-id>

:code:`--hard`
  Optional. Hard stop the instance

:code:`--timeout <timeout>`
  Optional. Time in seconds until the instance is hard stopped. Default: 60

:code:`<instance-id>`
  The instance ID
