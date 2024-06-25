:original_name: modelarts_05_0042.html

.. _modelarts_05_0042:

Is the Keras Engine Supported?
==============================

Notebook instances in **DevEnviron** support the Keras engine. The Keras engine is not supported in job training and model deployment (inference).

Keras is an advanced neural network API written in Python. It is capable of running on top of TensorFlow, CNTK, or Theano. Notebook instances in **DevEnviron** support **tf.keras**.

How Do I View Keras Versions?
-----------------------------

#. On the ModelArts management console, create a notebook instance with image **TensorFlow-1.13** or **TensorFlow-1.15**.

#. Access the notebook instance. In JupyterLab, run **!pip list** to view Keras versions.


   .. figure:: /_static/images/en-us_image_0000001910018922.png
      :alt: **Figure 1** Viewing Keras versions

      **Figure 1** Viewing Keras versions
