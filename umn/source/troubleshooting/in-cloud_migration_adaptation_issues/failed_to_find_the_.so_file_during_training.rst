:original_name: modelarts_13_0044.html

.. _modelarts_13_0044:

Failed to Find the .so File During Training
===========================================

Symptom
-------

During the execution of a ModelArts training job, the following error message is displayed in the log and the training failed:

.. code-block::

   libcudart.so.9.0 cannot open shared object file no such file or directory

Possible Cause
--------------

The CUDA version of the .so file generated during compilation is different from that of the training job.

Solution
--------

If the CUDA version in the compilation environment is different from that in the training environment, an error will occur when a training job runs. For example, this error occurs if the .so file generated in the TensorFlow 1.13 development environment of CUDA version 10 is used in the TensorFlow 1.12 training environment of CUDA version 9.0.

To resolve this issue, perform the following operations:

#. Add the following command before executing a training job to check whether the .so file is available. If the .so file is available, go to :ref:`2 <modelarts_13_0044__en-us_topic_0211827454_li5219740183811>`. Otherwise, go to :ref:`3 <modelarts_13_0044__en-us_topic_0211827454_li61211843611>`.

   .. code-block::

      import os;
      os.system(find /usr -name *libcudart.so*);

#. .. _modelarts_13_0044__en-us_topic_0211827454_li5219740183811:

   Configure the environment variable **LD_LIBRARY_PATH** and issue the training job again.

   For example, if the path for storing the .so file is **/use/local/cuda/lib64**, configure **LD_LIBRARY_PATH** as follows:

   .. code-block::

      export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64)

#. .. _modelarts_13_0044__en-us_topic_0211827454_li61211843611:

   Run the following command to check whether the CUDA version of the training environment supports the .so file:

   .. code-block::

      os.system("cat /usr/local/cuda/version.txt")

   a. If so, import an external .so file (download it from the browser) and configure **LD_LIBRARY_PATH** in :ref:`2 <modelarts_13_0044__en-us_topic_0211827454_li5219740183811>`.
   b. If not, replace the engine and issue the training job again. Alternatively, use a custom image to create a job. For details, see :ref:`Using a Custom Image to Train Models <docker-modelarts_0017>`.
