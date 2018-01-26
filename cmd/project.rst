project
=======

project create
--------------

Create a project

.. code::

   deli project create <name>

:code:`<name>`
  The project name

project delete
--------------

Delete a project

.. code::

   deli project delete <project-id>

:code:`<project-id>`
  The project ID

project inspect
---------------

Inspect a project

.. code::

   deli project inspect <project-id>

:code:`<project-id>`
  The project ID

project list
------------

List projects

.. code::

   deli project list
     --all

:code:`--all`
  Optional. Include projects you are not a member of

project member
--------------

project member add
^^^^^^^^^^^^^^^^^^

Add a member to a project

.. code::

   deli project member add <username> <driver>

:code:`<username>`
  The username of the user to add

:code:`<driver>`
  The drive of the user to add

project member inspect
^^^^^^^^^^^^^^^^^^^^^^

Inspect a project member

.. code::

   deli project member inspect <member-id>

:code:`<member-id>`
  The project member ID

project member list
^^^^^^^^^^^^^^^^^^^

List project members

.. code::

   deli project member list

project member remove
^^^^^^^^^^^^^^^^^^^^^

Remove a member from a project

.. code::

   deli project member remove <member-id>

:code:`<member-id>`
  The project member ID

project member update
^^^^^^^^^^^^^^^^^^^^^

Update a project member's roles

.. code::

   deli project member update
     --role-id <role-id>
     <member-id>

:code:`--role-id <role-id>`
  The role to give the member. Can be repeated multiple times.

:code:`<member-id>`
  The project member ID

project quota
-------------

project quota inspect
^^^^^^^^^^^^^^^^^^^^^

Inspect a project's quota

.. code::

   deli project quota inspect

project quota modify
^^^^^^^^^^^^^^^^^^^^

Modify a project's quota

.. code::

   deli project quota modify
     --vcpu <vcpu>
     --ram <ram>
     --disk <size>

:code:`--vcpu <vcpu>`
  The number of vcpus the project is allowed to use

:code:`--ram <ram>`
  The amount of ram (in MB) the project is allowed to use

:code:`--disk <size>`
  The amount of disk (in GB) the project is allowed to use
