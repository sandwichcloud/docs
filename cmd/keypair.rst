keypair
=======

keypair delete
--------------

Delete a keypair

.. code::

   deli keypair delete <keypair-id>

:code:`<keypair-id>`
  The keypair ID

keypair generate
----------------

Generate a keypair

.. code::

   deli keypair generate
     --key-dir <key-dir>
     <name>

:code:`--key-dir <key-dir>`
  Optional. Directory to save the keypair to. Default: ~/.ssh

:code:`<name>`
  They keypair name

keypair import
--------------

Import a keypair

.. code::

   deli keypair import
     <name>
     <public-key-file>

:code:`<name>`
  The keypair name

:code:`<public-key-file>`
  The public key file for the keypair

keypair inspect
---------------

Inspect a keypair

.. code::

   deli keypair inspect <keypair-id>

:code:`<keypair-id>`
  The keypair ID

keypair list
------------

List keypairs

.. code::

   deli keypair list
