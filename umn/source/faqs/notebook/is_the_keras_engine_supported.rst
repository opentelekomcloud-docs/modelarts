:original_name: modelarts_21_0065.html

.. _modelarts_21_0065:

Is the Keras Engine Supported?
==============================

Notebook instances in **DevEnviron** support the Keras engine. The Keras engine is not supported in job training and model deployment (inference).

Keras is an advanced neural network API written in Python. It is capable of running on top of TensorFlow, CNTK, or Theano. Notebook instances in **DevEnviron** support **tf.keras**.

How Do I View Keras Versions?
-----------------------------

#. On the ModelArts management console, create a notebook instance.

#. Click the notebook instance name to go to the **Jupyter** page. On the right of the page, click **New** and select **TensorFlow** to create a notebook instance.

#. In the notebook instance, run **!pip list** to view Keras versions.

   The following figure shows the Keras versions when **Python3** and **TensorFlow-1.8** are selected during notebook instance creation.


   .. figure:: /_static/images/en-us_image_0000001279905793.png
      :alt: **Figure 1** Viewing Keras versions

      **Figure 1** Viewing Keras versions
