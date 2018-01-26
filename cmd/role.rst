global-role
===========

global-role create
------------------

Create a global role

.. code::

   deli global-role create
     --policy <policy-name>
     <name>

:code:`--policy <policy-name>`
  Policy to add to the role. Can be repeated multiple times for multiple policies.

:code:`<name>`
  The global role name

global-role delete
-------------------

Delete a global role

.. code::

   deli global-role delete <global-role-id>

:code:`<global-role-id>`
  The global role ID

global-role inspect
-------------------

Inspect a global role

.. code::

   deli global-role inspect <global-role-id>

:code:`<global-role-id>`
  The global role ID

global-role list
----------------

List global roles

.. code::

   deli global-role list

global-role update
------------------

Update a global role

.. code::

   deli global-role update
     --policy <policy-name>
     <global-role-id>

:code:`--policy <policy-name>`
  Policy to add to the role. Can be repeated multiple times for multiple policies.

:code:`<global-role-id>`
  The global role ID

project-role
===========

project-role create
------------------

Create a project role

.. code::

   deli project-role create
     --policy <policy-name>
     <name>

:code:`--policy <policy-name>`
  Policy to add to the role. Can be repeated multiple times for multiple policies.

:code:`<name>`
  The project role name

project-role delete
-------------------

Delete a project role

.. code::

   deli project-role delete <project-role-id>

:code:`<project-role-id>`
  The project role ID

project-role inspect
-------------------

Inspect a project role

.. code::

   deli project-role inspect <project-role-id>

:code:`<project-role-id>`
  The project role ID

project-role list
----------------

List project roles

.. code::

   deli project-role list

project-role update
------------------

Update a project role

.. code::

   deli project-role update
     --policy <policy-name>
     <project-role-id>

:code:`--policy <policy-name>`
  Policy to add to the role. Can be repeated multiple times for multiple policies.

:code:`<project-role-id>`
  The project role ID
