:original_name: dataprepare-modelarts-0021.html

.. _dataprepare-modelarts-0021:

Processing Data
===============

After data is collected and imported, the data cannot directly meet the training requirements. Process data during R&D to ensure data quality and prevent negative impact on subsequent operations (such as data labeling and model training). ModelArts provides data processing to extract valuable and meaningful data from a large amount of disordered and difficult-to-understand data.

ModelArts provides four basic data processing functions:

-  Data validation: helps AI developers identify invalid data, such as damaged data and unqualified data, and effectively prevent algorithm precision deterioration or training failures caused by noisy data.
-  Data cleansing: checks data consistency based on data validation and correct some invalid values.
-  Data selection: During AI development, a large amount of duplicate data may exist in the collected data. The duplicate data does not improve the model precision. Moreover, it takes a long time to label the data. In this case, use data selection to preprocess data and deduplicate collected data.
-  Data augmentation: increases the data volume.
