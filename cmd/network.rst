network
=======

network create
--------------

Create a network

.. code::

   deli network create
     --region-id <region-id>
     --port-group <port-group>
     --cidr <cidr>
     --gateway <gateway>
     --dns-server <dns-server>
     --pool-start <pool-start>
     --pool-end <pool-end>
     <name>

:code:`--region-id <region-id>`
  The region to create the network in

:code:`--port-group <port-group>`
  The port group for the network

:code:`--cidr <cidr>`
  The network CIDR

:code:`--gateway <gateway>`
  The network gateway

:code:`--dns-server <dns-server>`
  DNS Server for the network. Can be repeated multiple times.

:code:`--pool-start <pool-start>`
  The address for the start of the IP pool

:code:`--pool-end <pool-end>`
  The address for the end of the IP pool

:code:`<name>`
  The network name

network delete
--------------

Delete a network

.. code::

   deli network delete <network-id>

:code:`<network-id>`
  The network ID

network inspect
---------------

Inspect a network

.. code::

   deli network inspect <network-id>

:code:`<network-id>`
  The network ID

network list
------------

List networks

.. code::

   deli network list

network port
------------

network port delete
^^^^^^^^^^^^^^^^^^^

Delete a network port delete

.. code::

   deli network port delete <network-port-id>

:code:`<network-port-id>`
  The network port ID

network port inspect
^^^^^^^^^^^^^^^^^^^^

Inspect a network port

.. code::

   deli network port inspect <network-port-id>

:code:`<network-port-id>`
  The network port ID

network port list
^^^^^^^^^^^^^^^^^

List network ports

.. code::

   deli network port list
