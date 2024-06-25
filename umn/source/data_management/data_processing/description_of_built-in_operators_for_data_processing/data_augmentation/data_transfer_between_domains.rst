:original_name: dataprocess-modelarts-00011.html

.. _dataprocess-modelarts-00011:

Data Transfer Between Domains
=============================

CycleGAN Operator Overview
--------------------------

CycleGAN operator generates images for domain transfer based on CycleGAN, that is, converts one type of images into another, or converts samples in the *X* space into samples in the *Y* space. CycleGAN can use non-paired data for training. During model training, two inputs are supported, indicating the source domain and target domain of data, respectively. After the training is complete, all images transferred from the source domain to the target domain are generated.

.. table:: **Table 1** Advanced parameters of the CycleGAN operator

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Default               | Description                                                                                                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================================================================================================+
   | do_validation         | True                  | Whether to validate data. The default value is **True**, which indicates that data is validated before being generated. **False** indicates data is generated directly.                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_channel         | 3                     | Number of channels of the image                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_height          | 256                   | Image height. The value must be 2 to the power of *n*.                                                                                                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_width           | 256                   | Image width. The value must be 2 to the power of *n*.                                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | batch_size            | 1                     | Number of samples for batch training                                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | max_epoch             | 100                   | Number of dataset epochs during training                                                                                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | g_learning_rate       | 0.0001                | Learning rate for the generator training                                                                                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | d_learning_rate       | 0.0001                | Learning rate for the discriminator training                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_frequency         | 5                     | Logging frequency (counted by step)                                                                                                                                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | save_frequency        | 5                     | Model save frequency (counted by epoch)                                                                                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | predict               | False                 | Whether to perform inference and prediction. The default value is **False**. If this parameter is set to **True**, you need to set **resume** to the OBS path where the trained model is stored.                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resume                | empty                 | If **predict** is set to **True**, enter the OBS path where the TensorFlow model file is stored for inference and prediction. Currently, only models in **.pb** format are supported. Example: **obs://xxx/xxxx.pb**. |
   |                       |                       |                                                                                                                                                                                                                       |
   |                       |                       | The default value is **empty**.                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Data Input
----------

The following two types of operator input are available:

-  **Datasets**: Select a dataset and its version created on the ModelArts console from the drop-down list. Ensure that the dataset type be the same as the scenario type selected in this task.
-  **OBSCatalog**: Operator image_generation does not require labeling information and its input supports single-level or dual-level directories, and the storage structure supports single-level or dual-level mode.

The single-level directory structure is as follows:

.. code-block::

   image_folder----0001.jpg
               ----0002.jpg
               ----0003.jpg
               ...
               ----1000.jpg

The dual-level directory structure is as follows:

.. code-block::

   image_folder----sub_folder_1----0001.jpg
                               ----0002.jpg
                               ----0003.jpg
                               ...
                               ----0500.jpg
               ----sub_folder_2----0001.jpg
                               ----0002.jpg
                               ----0003.jpg
                               ...
                               ----0500.jpg
                               ...
               ----sub_folder_100----0001.jpg
                                 ----0002.jpg
                                 ----0003.jpg
                                 ...
                                 ----0500.jpg

Output Description
------------------

The output directory structure is as follows: The folder **model** stores model **frozen PB** for inference, the folder **samples** stores the output images during training, and the folder **Data** stores the images generated by the training model.

.. code-block::

   train_url----model----CYcleGan_epoch_10.pb
                     ----CYcleGan_epoch_20.pb
                     ...
                     ----CYcleGan_epoch_1000.pb
            ----samples----0000_0.jpg
                      ----0000_1.jpg
                      ...
                      ----0100_15.jpg
            ----Data----CYcleGan_0_0.jpg
                    ----CYcleGan_0_1.jpg
                    ...
                    ----CYcleGan_16_8.jpg
            ----output_0.manifest

A manifest file example is as follows:

.. code-block::

   {
       "id": "xss",
       "source": "obs://home/fc8e2688015d4a1784dcbda44d840307_14.jpg",
       "usage": "train",
       "annotation": [
           {
               "name": "Cat",
               "type": "modelarts/image_classification"
           }
       ]
   }
