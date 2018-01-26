zone
====

zone create
-----------

Create a zone

.. code::

   deli zone create
     --region-id <region-id>
     --vm-cluster <vm-cluster>
     --vm-datastore <vm-datastore>
     --vm-folder <vm-folder>
     --core-provision-percent <core-provision-percent>
     --ram-provision-percent <ram-provision-percent>

:code:`--region-id <region-id>`
  The region this zone belongs to

:code:`--vm-cluster <vm-cluster>`
  The VMware cluster for this zone

:code:`--vm-datastore <vm-datastore>`
  The VMware datastore for this zone

:code:`--vm-folder <vm-folder>`
  Optional. The VMware VM & Templates folder to keep vms in

:code:`--core-provision-percent <core-provision-percent>`
  Optional. The percentage of cores to provision from the VMware cluster. Default: 1600

:code:`--ram-provision-percent <ram-provision-percent>`
  Optional. The percentage of ram to provision from the VMware cluster. Default: 150

zone delete
-----------

Delete a zone

.. code::

   deli zone delete <zone-id>

:code:`<zone-id>`
  The zone ID

zone inspect
------------

Inspect a zone

.. code::

   deli zone inspect <zone-id>

:code:`<zone-id>`
  The zone ID

zone list
---------

List zones

.. code::

   deli zone list
     --region-id <region-id>

:code:`--region-id <region-id>`
  Optional. The region ID to filter by

zone update
-----------

Update a zone

.. code::

   deli zone update
     --[no-]schedulable
     <zone-id>

:code:`--[no-]schedulable`
  Enable or disable the ability to schedule workloads in the zone

:code:`<zone-id>`
  The zone ID
