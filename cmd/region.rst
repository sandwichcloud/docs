region
======

region create
-------------

Create a region

.. code::

   deli region create
     --datacenter <datacenter>
     --image-datastore <datastore>
     --image-folder <image-folder>
     <name>

:code:`--datacenter <datacenter>`
  The VMware Datacenter for the region

:code:`--image-datastore <datastore>`
  The VMware Datastore to keep images in

:code:`--image-folder <image-folder>`
  Optional. The VMware VM & Tempaltes folder to keep images in

:code:`<name>`
  The region name

region delete
-------------

Delete a region

.. code::

   deli region delete <region-id>

:code:`<region-id>`
  The region ID

region inspect
--------------

Inspect a region

.. code::

   deli region inspect <region-id>

:code:`<region-id>`
  The region ID

region list
-----------

List regions

.. code::

   deli region list

region update
-------------

Update a region

.. code::

   deli region update
     --[no-]schedulable
     <region-id>

:code:`--[no-]schedulable`
  Enable or disable the ability to schedule workloads in the region

:code:`<region-id>`
  The region ID
