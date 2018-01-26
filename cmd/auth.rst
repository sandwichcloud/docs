auth
====

auth login
----------

Login to the Sandwich Cloud API

.. code::

   deli auth login
     --method <method>
     --username <username>
     --password <password>

:code:`--method <method>`
  Method to use for auth. If not given uses the API default.

:code:`-u | --username <username>`
  The username to auth with.

:code:`-p | --paswword <password>`
  User password to auth with. If not given, will prompt for input

.. note::

   Some auth methods may not require a username or password.

auth info
---------

Show information about the current auth tokens

.. code::

   deli auth info <type>

:code:`<type>`
  The type of token to view information from (scoped or unscoped)

auth scope
----------

Scope the current auth token to a project

.. code::

   deli auth scope <project-id>

:code:`<project-id>`
  The project id to scope to
