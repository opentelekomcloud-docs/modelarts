:original_name: dataprocess-modelarts-00010.html

.. _dataprocess-modelarts-00010:

Data Generation
===============

Introduction to Data Generation
-------------------------------

The image generation uses a generative adversarial network (GAN) to generate a new dataset with the existing dataset. A GAN is a network that contains a generator and discriminator. The generator randomly selects samples from a latent space as the input, and outputs results similar to the real samples in the training set. The discriminator distinguishes the outputs of the generative network from the real samples by inputting real samples or outputs of the generative network. The generative network's training objective is to increase the error rate of the discriminative network (that is, "fool" the discriminative network). The two networks contest with each other and continuously adjust parameters to achieve the final purpose, that is, make the discriminative network unable to distinguish whether the output of the generative network is true. The generative network obtained during training can be used to generate images similar to the input images, which can be used as new datasets for training. New datasets generated based on GANs have no labels. Original data is not changed during image generation. The newly generated image or XML file is saved in the specified output path.

StyleGAN Operator Overview
--------------------------

StyleGAN operator randomly generates similar images based on StyleGAN2 when a dataset is small. StyleGAN has a new generator architecture that can control the high-level attributes such as hairstyle and freckles of the generated images. These generated images perform even better in certain aspects. In addition, StyleGAN is equipped with the data augmentation algorithm, which can generate new satisfactory samples even with a small number of samples. However, there must be at least 70 samples to have rich image styles.

.. table:: **Table 1** Advanced parameters of the StyleGAN operator

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Name                  | Default               | Description                                                                                                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================================================================================================+
   | resolution            | 256                   | Height and width of the generated square image. The value must be 2 to the power of *n*.                                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | batch-size            | 8                     | Number of samples for batch training                                                                                                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | total-kimg            | 300                   | The total number of trained images is obtained by multiplying this parameter value by 1,000.                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | generate_num          | 300                   | Number of generated images. If the generated images have multiple classes, the value is the number of generated images of each class.                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | predict               | False                 | Whether to perform inference and prediction. The default value is **False**. If this parameter is set to **True**, you need to set **resume** to the OBS path where the trained model is stored.                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resume                | empty                 | If **predict** is set to **True**, enter the OBS path where the TensorFlow model file is stored for inference and prediction. Currently, only models in **.pb** format are supported. Example: **obs://xxx/xxxx.pb**. |
   |                       |                       |                                                                                                                                                                                                                       |
   |                       |                       | The default value is **empty**.                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | do_validation         | True                  | Whether to validate data. The default value is **True**, which indicates that data is validated before being generated. **False** indicates data is generated directly.                                               |
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
