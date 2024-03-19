:original_name: docker-modelarts_0029.html

.. _docker-modelarts_0029:

Migrating an Image to ModelArts Training
========================================

To migrate an image to the new training management version, perform the following operations:

#. Add the default user group **ma-group** (**GID** = **100**) for the image of the new-version training management. If the user group whose **GID** is **100** exists, skip this step.
#. Add the default user **ma-user** (**UID** = **1000**) for the image of the new-version training management. If the user whose **UID** is **1000** exists, skip this step.
#. Modify the permission on files in the image to allow **ma-user** whose **UID** is **1000** to read and write the files.

You can modify an image by referring to the following Dockerfile so that the image complies with specifications for custom images of the new-version training management.

.. code-block::

   FROM {An existing image}

   USER root

   RUN groupadd ma-group -g 100 && \
       useradd -d /home/ma-user -m -u 1000 -g 100 -s /bin/bash ma-user

   # [important] avoid missing training log
   ENV PYTHONUNBUFFERED=1

   USER ma-user
   WORKDIR /home/ma-user

In the new-version training management, custom images are executed by the user whose **UID** is **1000** by default. Before using an image in the new-version training management, check image file permissions on the server where the image was built. The process is as follows:

Run the following command to specify the user whose **UID** is **1000** to run the image:

.. code-block::

   docker run -u 1000 -ti {Custom image} bash

Run the boot command (such as the following command) in the container during image runtime:

.. code-block::

   python train.py

Check whether there are any **Permission denied** error.

If **Permission denied** is displayed for a file, for example, **train.py**, run the following command to change the file that belongs to the user whose **UID** is **1000**:

.. code-block::

   chown 1000 train.py
