:original_name: modelarts_05_0380.html

.. _modelarts_05_0380:

How Do I Obtain **RANK_TABLE_FILE** on ModelArts for Distributed Training?
==========================================================================

ModelArts automatically provides the **RANK_TABLE_FILE** file for you. Obtain the file location through environment variables.

-  Open the notebook terminal and run the following command to view **RANK_TABLE_FILE**:

   ::

      env | grep RANK

-  In a training job, add the following code to the first line of the training startup script to print the value of **RANK_TABLE_FILE**:

   ::

      os.system('env | grep RANK')
