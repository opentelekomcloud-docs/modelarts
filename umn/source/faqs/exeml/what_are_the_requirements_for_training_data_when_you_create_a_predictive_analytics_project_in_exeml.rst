:original_name: modelarts_21_0062.html

.. _modelarts_21_0062:

What Are the Requirements for Training Data When You Create a Predictive Analytics Project in ExeML?
====================================================================================================

Requirements on Datasets
------------------------

-  Data files cannot be stored in the root directory of an OBS bucket.
-  The name of files in a dataset consists of letters, digits, hyphens (-), and underscores (_), and the file name extension is CSV.
-  The files are saved in CSV format. Use newline characters (\\n or LF) to separate lines and commas (,) to separate columns of the file content. The column content cannot contain special characters such as commas (,) and newline characters. The quotation marks are not supported. It is recommended that the column content consist of letters and digits.
-  The number of columns in the training data must be the same, and the total number of data records must be greater than or equal to 100. The training columns cannot contain data of the timestamp format (such as yy-mm-dd or yyyy-mm-dd). If you select continuous values for a label column, ensure that the column contains only digits and the training data has at least 25 different values. The training data CSV file cannot contain the table header. Otherwise, the training fails.
