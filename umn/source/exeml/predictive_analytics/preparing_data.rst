:original_name: modelarts_21_0015.html

.. _modelarts_21_0015:

Preparing Data
==============

Before using ModelArts to build a predictive analytics model, upload data to OBS.

Uploading Data to OBS
---------------------

This operation uses the OBS client to upload data. For more information about how to create a bucket and upload files, see `Creating a Bucket <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0306.html>`__ and `Uploading a File <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0307.html>`__.

Perform the following operations to import data to the dataset for model training and building.

#. Log in to OBS Console and `create a bucket <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0306.html>`__
#. `Upload the local data <https://docs.otc.t-systems.com/en-us/usermanual/obs/obs_03_0307.html>`__ to the OBS bucket. If you have a large amount of data, you are advised to use OBS Browser+ to upload data or folders. The uploaded data must meet the dataset requirements of the ExeML project.

Requirements on Datasets
------------------------

-  The name of files in a dataset consists of letters, digits, hyphens (-), and underscores (_), and the file name extension is CSV. The files cannot be stored in the root directory of an OBS bucket, but in a folder in the OBS bucket, for example, **/obs-xxx/data/input.csv**.
-  The files are saved in CSV format. Use newline characters (\\n) to separate lines and commas (,) to separate columns of the file content. The file content cannot contain Chinese characters. The column content cannot contain special characters such as commas (,) and newline characters. The quotation marks are not supported. It is recommended that the column content consist of letters and digits.
-  The number of training columns is the same. There are at least 100 different data records (a feature with different values is considered as different data) in total. The training columns cannot contain the data of the timestamp format (such as yy-mm-dd and yyyy-mm-dd). If a column has only one value, the column is considered invalid and discarded. Ensure that the dataset contains at least two valid columns except the label column. If you select continuous values for a label column, ensure that the column contains only digits and the training data has at least 25 different values. The training data CSV file cannot contain the table header. Otherwise, the training fails.

Requirements for Files Uploaded to OBS
--------------------------------------

The OBS path of the predictive analytics projects must comply with the following rules:

-  The OBS path of the input data must redirect to the data files. The data files must be stored in a folder in an OBS bucket rather than the root directory of the OBS bucket, for example, **/obs-xxx/data/input.csv**.
-  The input data must be in CSV format. The data files do not contain the table header and the number of valid data lines must be greater than 150.

Predictive Analytics File Example
---------------------------------

Example: Predict whether customers would be interested in a time deposit based on their characteristics.

.. table:: **Table 1** Parameters and meanings of data sources

   ========= ================ ======= ================================
   Parameter Meaning          Type    Description
   ========= ================ ======= ================================
   attr_1    Age              Integer Age of the customer
   attr_2    Occupation       String  Occupation of the customer
   attr_3    Marital status   String  Marital status of the customer
   attr_4    Education status String  Education status of the customer
   attr_5    Real estate      String  Real estate of the customer
   attr_6    Loan             String  Loan of the customer
   attr_7    Deposit          String  Deposit of the customer
   ========= ================ ======= ================================

.. table:: **Table 2** Sample data

   ====== ============ ======= ========= ====== ====== ======
   attr_1 attr_2       attr_3  attr_4    attr_5 attr_6 attr_7
   ====== ============ ======= ========= ====== ====== ======
   58     management   married tertiary  yes    no     no
   44     technician   single  secondary yes    no     no
   33     entrepreneur married secondary yes    yes    no
   47     blue-collar  married unknown   yes    no     no
   33     unknown      single  unknown   no     no     no
   35     management   married tertiary  yes    no     no
   ====== ============ ======= ========= ====== ====== ======
