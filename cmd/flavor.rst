flavor
======

flavor create
-------------

Create a flavor

.. code::

   deli flavor create
     --vcpus <vcpus>
     --ram <ram>
     --disk <disk>
     <name>

:code:`--vcpus <vcpus>`
  Number of VCPUs for the flavor

:code:`--ram <ram>`
  Amount of ram in megabytes for the flavor

:code:`--disk <disk>`
  Size in gigabytes of the root disk for the flavor

:code:`<name>`
  The flavor name

flavor delete
-------------

Delete a flavor

.. code::

   deli flavor delete <flavor-id>

:code:`<flavor-id>`
  The flavor ID

flavor inspect
--------------

Inspect a flavor

.. code::

   deli flavor inspect <flavor-id>

:code:`<flavor-id>`
 The flavor ID

flavor list
-----------

List flavors

.. code::

   deli flavor list
