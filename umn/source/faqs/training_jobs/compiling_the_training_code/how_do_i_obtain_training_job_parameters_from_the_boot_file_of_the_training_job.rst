:original_name: modelarts_05_0093.html

.. _modelarts_05_0093:

How Do I Obtain Training Job Parameters from the Boot File of the Training Job?
===============================================================================

Training job parameters can be automatically generated in the background or you can enter them manually. To obtain training job parameters:

#. When a training job is created, **train_url** in the running parameters of the training job indicates where the training results are output to, and **data_url** indicates a data source. The **test** parameter is entered manually.

#. After the training job is executed, you can click the job name in the training job list to view its details. You can obtain the parameter input mode from logs, as shown in :ref:`Figure 1 <en-us_topic_0000001943977449__fig74929528456>`.

   .. _en-us_topic_0000001943977449__fig74929528456:

   .. figure:: /_static/images/en-us_image_0000001910018798.png
      :alt: **Figure 1** Viewing logs

      **Figure 1** Viewing logs

#. To obtain the values of **train_url**, **data_url**, and **test** during training, add the following code to the boot file of the training job:

   .. code-block::

      import argparse
      parser = argparse.ArgumentParser()
      parser.add_argument('--data_url', type=str, default=None, help='test')
      parser.add_argument('--train_url', type=str, default=None, help='test')
      parser.add_argument('--test', type=str, default=None, help='test')
