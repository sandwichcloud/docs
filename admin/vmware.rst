VMware
======

Account Permissions
-------------------

Firewall
--------

All hosts in all Clusters connected to Sandwich Cloud Zones must allow the following
firewall rule :code:`VM serial port connected to vSPC`.

All hosts must also be able to communicate with the Sandwich Cloud Metadata Service.

VMotion
-------

Regular
^^^^^^^

Feel free to VMotion VMs to different hosts to balance out your clusters.

.. warning::

   VMs must be kept within the same Compute Cluster. If they are not Sandwich
   Cloud may loose track of the VM and any action performed may result in
   unexpected behavior.

Storage
^^^^^^^^

**DO NOT** Storage VMotion VMs. If you are migrating to a new datastore
please see `Migrating Datastores`_.

Maintenance
-----------

Migrating Datastores
^^^^^^^^^^^^^^^^^^^^

Regions
~~~~~~~

Migrating a Region's Image Datastore requires a new Region to be created. This
requires building out the new Region, importing images and redeploying VMs and Volumes.

#. Create a new Region connected to the new Image Datastore
#. Create new Zones in the new Region and enable scheduling.
#. Enable scheduling into the new Region.
#. Disable scheduling into the old Region.
#. Import images into the new Region.
#. Deploy replacement VMs into the new Region.
#. Decommission Zones in the old Region.

Zones
~~~~~

Migrating a Zone's VM Datastore requires a new Zone to be created. This requires
redeploying VMs and Volumes into the new Region.

#. Create a new zone connected to the same Compute Cluster but with the new VM Datastore.
#. Enable scheduling into the new Zone.
#. Disable scheduling into the old Zone.
#. Deploy replacement VMs into the new Zone.
#. Delete the old Zone.
