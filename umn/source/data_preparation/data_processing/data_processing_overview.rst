:original_name: dataprocess-modelarts-00001.html

.. _dataprocess-modelarts-00001:

Data Processing Overview
========================

ModelArts provides the data processing function to extract valuable and meaningful data from a large amount of disordered and difficult-to-understand data. After data is collected and accessed, the data cannot directly meet the training requirements. Process data during R&D to ensure data quality and prevent negative impact on subsequent operations (such as data labeling and model training).

Common data processing types are as follows:

-  :ref:`Data validation <dataprocess-modelarts-00003>`: Generally, data needs to be validated after being collected to ensure data validity.

   Data validation is a process of determining and verifying data availability. Generally, the collected data cannot be further processed due to some format problems. Take image recognition as an example. Users often find some images from the Internet for training, and the image quality cannot be ensured. The name, path, and extension of the images may not meet the requirements of the training algorithm. Images may also be partially damaged. As a result, the images cannot be decoded or processed by the algorithm. Therefore, data validation is very important. It helps AI developers detect data problems and effectively prevent algorithm precision deterioration or training failures caused by noisy data.

-  :ref:`Data cleansing <dataprocess-modelarts-00004>`: refers to the process of removing, correcting, or supplementing data.

   Data cleansing is to check data consistency based on data validation and correct some invalid values. For example, in the deep learning field, data may be cleansed based on a positive sample and a negative sample that are input by a user, to retain a category that the user wants and remove a category that the user does not want.

-  :ref:`Data selection <dataprocess-modelarts-00005>`: refers to the process of selecting data subsets from full data.

   Data can be selected based on the similarity or deep learning algorithm. Data selection can avoid problems such as duplicate and similar images introduced during manual image collection. Among a batch of inference data input to an old model, data selection using built-in rules can further improve the precision of the old model.

-  Data augmentation:

   :ref:`Data augmentation <dataprocess-modelarts-00009>`: increases data volumes directly or indirectly through simple data augmentation operations such as scaling, cropping, transformation, and composition.

   :ref:`Data transfer between domains <dataprocess-modelarts-00011>`: generates data transferred from the original domain to the target domain by applying deep learning models and learning the datasets of the original and target domains.
