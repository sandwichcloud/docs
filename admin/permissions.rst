Policies and Roles
==================

Policies
--------

Policies
^^^^^^^^

:code:`policies:get`
  Ability to get a policy

:code:`policies:list`
  Ability to list policies

Roles
^^^^^

:code:`roles:global:create`
  Ability to create a global role

:code:`roles:project:create`
  Ability to create a project role

:code:`roles:global:get`
  Ability to get a global role

:code:`roles:project:get`
  Ability to get a project role

:code:`roles:global:list`
  Ability to list global roles

:code:`roles:project:list`
  Ability to list project roles

:code:`roles:global:update`
  Ability to update a global role

:code:`roles:project:update`
  Ability to update a project role

:code:`roles:global:delete`
  Ability to delete a global role

:code:`roles:project:create`
  Ability to delete a project role

Flavors
^^^^^^^

:code:`flavors:create`
  Ability to create a flavor

:code:`flavors:get`
  Ability to get a flavor

:code:`flavors:list`
  Ability to list flavors

:code:`flavors:delete`
  Ability to delete a flavor

Regions
^^^^^^^

:code:`regions:create`
  Ability to create a region

:code:`regions:get`
  Ability to get a region

:code:`regions:list`
  Ability to list regions

:code:`regions:delete`
  Ability to delete a region

:code:`regions:action:schedule`
  Ability to change the schedule mode of the region

Zones
^^^^^

:code:`zones:create`
  Ability to create a zone

:code:`zones:get`
  Ability to get a zone

:code:`zones:list`
  Ability to list zones

:code:`zones:delete`
  Ability to delete a zone

:code:`zones:action:schedule`
  Ability to change the schedule mode of the zone

Projects
^^^^^^^^

:code:`projects:create`
  Ability to create a project

:code:`projects:get`
  Ability to get a project

:code:`projects:get:all`
  Ability to get all projects

:code:`projects:list`
  Ability to list projects

:code:`projects:list:all`
  Ability to list all projects

:code:`projects:delete`
  Ability to delete a project

:code:`projects:scope`
  Ability to scope to a project

:code:`projects:scope:all`
  Ability to scope to all projects

:code:`projects:members:add`
  Ability to add a member to a project

:code:`projects:members:get`
  Ability to get a member in a project

:code:`projects:members:list`
  Ability to list members in a project

:code:`projects:members:modify`
  Ability to modify a project member's roles

:code:`projects:members:remove`
  Ability to remove a member from a project

:code:`projects:quota:get`
  Ability to get a project's quota

:code:`projects:quota:modify`
  Ability to modify a project's quota

Volumes
^^^^^^^

:code:`volumes:create`
  Ability to create a volume

:code:`volumes:get`
  Ability to get a volume

:code:`volumes:list`
  Ability to list volumes

:code:`volumes:delete`
  Ability to delete a volume

:code:`volumes:action:attach`
  Ability to attach a volume to an instance

:code:`volumes:action:detach`
  Ability to detach a volume from an instance

:code:`volumes:action:grow`
  Ability to grow a volume

:code:`volumes:action:clone`
  Ability to clone a volume

Images
^^^^^^

:code:`images:create`
  Ability to create an image

:code:`images:get`
  Ability to get an image

:code:`images:list`
  Ability to list images

:code:`images:delete`
  Ability to delete an image

:code:`images:action:visibility`
  Ability to change an image's visibility

:code:`images:action:visibility:public`
  Ability to change an image's visibility to public

:code:`images:action:lock`
  Ability to lock an image

:code:`images:action:unlock`
  Ability to unlock an image

:code:`images:members:add`
  Ability to add a member to an image

:code:`images:members:list`
  Ability to list an image's members

:code:`images:members:delete`
  Ability to delete a member from an image

Instances
^^^^^^^^^

:code:`instances:create`
  Ability to create an instance

:code:`instances:get`
  Ability to get an instance

:code:`instances:list`
  Ability to list instances

:code:`instances:delete`
  Ability to delete an instance

:code:`instances:action:stop`
  Ability to stop an instance

:code:`instances:action:start`
  Ability to start an instance

:code:`instances:action:restart`
  Ability to restart an instance

:code:`instances:action:image`
  Ability to create an image from an instance

Networks
^^^^^^^^

:code:`networks:create`
  Ability to create a network

:code:`networks:get`
  Ability to get a network

:code:`networks:list`
  Ability to list networks

:code:`networks:delete`
  Ability to delete a network

Service Accounts
^^^^^^^^^^^^^^^^

:code:`service_accounts:create`
  Ability to create a service account

:code:`service_accounts:get`
  Ability to get a service account

:code:`service_accounts:list`
  Ability to list service accounts

:code:`service_accounts:update`
  Ability to update a service account

:code:`service_accounts:delete`
  Ability to delete a service account

Keypairs
^^^^^^^^

:code:`keypairs:create`
  Ability to create a keypair

:code:`keypairs:get`
  Ability to get a keypair

:code:`keypairs:list`
  Ability to list keypairs

:code:`keypairs:delete`
  Ability to delete a keypair

Network Ports
^^^^^^^^^^^^^

:code:`network_ports:get`
  Ability to get a network port

:code:`network_ports:list`
  Ability to list network ports

:code:`network_ports:delete`
  Ability to delete a network port

Database Users
^^^^^^^^^^^^^^

:code:`database:users:create`

:code:`database:users:get`

:code:`database:users:list`

:code:`database:users:delete`

:code:`database:users:password`

:code:`database:users:roles:update`

Roles
-----

Global Roles
^^^^^^^^^^^^

Admin Role
~~~~~~~~~~

The administrative role for Sandwich Cloud. This role has access to all API
endpoints.

Project Roles
^^^^^^^^^^^^^

Project roles can only have policies that are for project based resources.

Default Member
~~~~~~~~~~~~~~

This is the default role for all project members. This role has access to all
scoped API endpoints.

Default Service Account
~~~~~~~~~~~~~~~~~~~~~~~

This is the default service account role for all project service accounts. This
role has access to read-only scoped API endpoints.
