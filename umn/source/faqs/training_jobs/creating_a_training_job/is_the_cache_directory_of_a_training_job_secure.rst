:original_name: modelarts_05_0098.html

.. _modelarts_05_0098:

Is the /cache Directory of a Training Job Secure?
=================================================

The program of a ModelArts training job runs in a container. The address of a directory to which the container is mounted is unique, and can be accessed only by the running container. Therefore, the **/cache** directory of the training job is secure.
