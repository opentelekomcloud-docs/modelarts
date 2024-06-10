:original_name: modelarts_23_0351.html

.. _modelarts_23_0351:

Preparing Data
==============

ModelArts uses OBS to store data, and backs up and takes snapshots for models, achieving secure, reliable storage at low costs.

-  :ref:`OBS <modelarts_23_0351__en-us_topic_0000001180077347_section81631146162713>`
-  :ref:`Obtaining Training Data <modelarts_23_0351__en-us_topic_0000001180077347_section471310416365>`

.. _modelarts_23_0351__en-us_topic_0000001180077347_section81631146162713:

OBS
---

OBS provides stable, secure, and efficient cloud storage service that lets you store virtually any volume of unstructured data in any format. Bucket and objects are basic concepts in OBS. A bucket is a container for storing objects in OBS. Each bucket is specific to a region and has specific storage class and access permissions. A bucket is accessible through its domain name over the Internet. An object is the basic unit of data storage in OBS.

OBS is a data storage center for ModelArts. All the input data, output data, and cache data during AI development can be stored in OBS buckets for reading.

Before using ModelArts, create an OBS bucket and folders for storing data.


.. figure:: /_static/images/en-us_image_0000001799498852.png
   :alt: **Figure 1** OBS

   **Figure 1** OBS

.. _modelarts_23_0351__en-us_topic_0000001180077347_section471310416365:

Obtaining Training Data
-----------------------

Use either of the following methods to obtain ModelArts training data:

-  Datasets stored in OBS buckets

   After labeling and preprocessing your dataset, upload it to an OBS bucket. When you create a training job, set **Training Input** to the path of the OBS bucket where the training data is stored.

-  Datasets in data management

   If your dataset has not labeled or requires preprocessing, import it to ModelArts data management for data preprocessing.


.. figure:: /_static/images/en-us_image_0000001799339076.png
   :alt: **Figure 2** Preparing data

   **Figure 2** Preparing data
