volume
======

volume create
-------------

Create a volume

.. code::

   deli volume create
     --zone-id <zone-id>
     --size <size>
     <name>

:code:`--zone-id <zone-id>`
  The zone tp create the volume in

:code:`--size <size>`
  The size of the volume in gigabytes

:code:`<name>`
  The volume name

volume delete
-------------

Delete a volume

.. code::

   deli volume delete <volume-id>

:code:`<volume-id>`
  The volume ID

volume inspect
--------------

Inspect a volume

.. code::

   deli volume inspect <volume-id>

:code:`<volume-id>`
  The volume ID

volume list
-----------

List volumes

.. code::

   deli volume list

volume attach
-------------

Attach a volume to an instance

.. code::

   deli volume attach <volume-id> <instance-id>

:code:`<volume-id>`
  The volume ID

:code:`<instance-id>`
  The instance ID

volume clone
------------

Clone a volume

.. code::

   deli volume clone <volume-id>

:code:`<volume-id>`
  The volume ID

volume detach
-------------

Detach a volume from an instance

.. code::

   deli volume detach <volume-id>

:code:`<volume-id>`
  The volume ID

volume grow
-----------

Increase the size of a volume

.. code::

   deli volume grow <volume-id> <size>

:code:`<volume-id>`
  The volume ID

:code:`<size>`
  The size of the volume in gigabytes
