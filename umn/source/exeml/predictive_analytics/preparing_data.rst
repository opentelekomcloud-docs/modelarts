:original_name: modelarts_21_0015.html

.. _modelarts_21_0015:

Preparing Data
==============

Before using ModelArts to build a predictive analytics model, upload data to OBS.

Uploading Data to OBS
---------------------

This operation uses the OBS client to upload data. For more information about how to create a bucket and upload files, see "Creating a Bucket" and "Uploading an Object".

Perform the following operations to import data to the dataset for model training and building.

#. Log in to OBS Console and create a bucket.
#. Upload a file to the OBS bucket. If you have a large amount of data, use OBS Browser+ to upload data or folders. The uploaded data must meet the dataset requirements of the ExeML project.

Requirements on Datasets
------------------------

-  The name of a file in a dataset consists of letters, digits, hyphens (-), and underscores (_), and the file name extension is CSV. The files cannot be stored in the root directory of an OBS bucket, but in a folder in the OBS bucket, for example, **/obs-xxx/data/input.csv**.
-  The files are saved in CSV format. Use newline characters (\\n) to separate lines and commas (,) to separate columns in the file. The column content cannot contain special characters such as commas (,) and newline characters (\\n). The quotation marks are not supported. It is recommended that the column content consist of letters and digits.
-  Data training

   -  The number of training columns is the same. There are at least 100 different data records in total (a feature with different values is considered as different data).
   -  The training columns cannot contain timestamp data (such as yy-mm-dd or yyyy-mm-dd).
   -  If a column has only one value, the column is considered invalid. Ensure that there are at least two values in the label column and no data is missing.

      .. note::

         The label column is the training target specified in a training task. It is the output (prediction item) for the model trained using the dataset.

   -  In addition to the label column, the dataset must contain at least two valid feature columns. Ensure that there are at least two values in each feature column and that the percentage of missing data must be lower than 10%.
   -  The training data in CSV file cannot contain the table header. Otherwise, the training fails.
   -  Due to the limitation of the feature filtering algorithm, place the label column in the last column of the dataset. Otherwise, the training may fail.

Requirements for Files Uploaded to OBS
--------------------------------------

The OBS path of the predictive analytics projects must comply with the following rules:

-  The OBS path of the input data must redirect to the data files. The data files must be stored in a folder in an OBS bucket rather than the root directory of the OBS bucket, for example, **/obs-xxx/data/input.csv**.
-  The input data must be in CSV format. The data files do not contain the table header and the number of valid data lines must be greater than 100. The number of columns must be less than 200, and the total data size cannot exceed 100 MB.

Predictive Analytics File Example
---------------------------------

Take the iris dataset as an example. Predict an iris species based on the lengths and widths of the iris calyx and petal.

.. table:: **Table 1** Parameters and meanings of data sources

   ========= ============ ====== ===============================
   Parameter Meaning      Type   Description
   ========= ============ ====== ===============================
   attr_1    Calyx length Double Length of the target iris calyx
   attr_2    Calyx width  Double Width of the target calyx
   attr_3    Petal length Double Length of the target iris petal
   attr_4    Petal width  Double Width of the target iris petal
   attr_5    Species      String Species of the iris
   ========= ============ ====== ===============================

.. table:: **Table 2** Sample data

   ====== ====== ====== ====== ===============
   attr_1 attr_2 attr_3 attr_4 attr_5
   ====== ====== ====== ====== ===============
   5.1    3.5    1.4    0.2    Iris-setosa
   7      3.2    4.7    1.4    Iris-versicolor
   6.3    3.3    6      2.5    Iris-virginica
   ====== ====== ====== ====== ===============
