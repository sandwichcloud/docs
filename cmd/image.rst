image
=====

image delete
------------

Delete an image

.. code::

   deli image delete <image-id>

:code:`<image-id>`
  The image ID

image import
------------

Import an image

.. code::

   deli image import
     --region-id <region-id>
     <name>
     <file-name>

:code:`--region-id <region-id>`
  The region to import the image into

:code:`<name>`
  The image name

:code:`<file-name>`
  The image's VMware Template name.

image inspect
-------------

Inspect an image

.. code::

   deli image inspect <image-id>

:code:`<image-id>`
  The image ID

image list
----------

List images

.. code::

   deli image list
     --visibility <visibility>

:code:`--visibility <visibility>`
  The visibility to filter by (PUBLIC, PRIVATE>)

image lock
----------

image unlock
------------

image visibility
----------

Change the visibility of an image

.. code::

   deli image visibility
     --[no-]public
     <image-id>

:code:`--[no-]public`
  Enable or disable public visibility of an image

:code:`<image-id>`
  The image ID

image member
------------

image member add
^^^^^^^^^^^^^^^^

Add a project as a member of the image

.. code::

   deli image member add
     <image-id>
     <project-id>

:code:`<image-id>`
  The image ID

:code:`<project-id>`
  The project ID

image member remove
^^^^^^^^^^^^^^^^^^^

Remove a project from an image

.. code::

   deli image member remove
     <image-id>
     <project-id>

:code:`<image-id>`
 The image ID

:code:`<project-id>`
 The project ID

image member list
^^^^^^^^^^^^^^^^^

List an image's members

.. code::

   deli image member list <image-id>

:code:`<image-id>`
  Optional. The image ID
