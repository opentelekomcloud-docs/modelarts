:original_name: modelarts_05_0381.html

.. _modelarts_05_0381:

How Do I Obtain the CUDA and cuDNN Versions of a Custom Image?
==============================================================

Obtain a CUDA version:

.. code-block::

   cat /usr/local/cuda/version.txt

Obtain a cuDNN version:

.. code-block::

   cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
