:original_name: modelarts_13_0025.html

.. _modelarts_13_0025:

Error Message "No space left" Displayed When a Multi-node TensorFlow Job Downloads Data to **/cache**
=====================================================================================================

Symptom
-------

During training job creation, error message "No space left" is displayed when a TensorFlow multi-node job downloads data to **/cache**.

Possible Cause
--------------

In a TensorFlow multi-node job, the **parameter server** (ps) and **worker** roles are started. The **ps** and **worker** roles are scheduled to the same machine. Training data is useless for **ps**. Therefore, the ps-related logic in code does not need to download the training data. If **ps** also downloads data to **/cache**, the actually downloaded data will be doubled. For example, if only 2.5 TB data is downloaded, the program displays a message indicating that space is insufficient because the **/cache** has only 4 TB available space.

Solution
--------

When a TensorFlow multi-node job is used to download data, the correct download logic is as follows:

.. code-block::

   import argparse
   parser = argparse.ArgumentParser()
   parser.add_argument("--job_name", type=str, default="")
   args = parser.parse_known_args()

   if args[0].job_name != "ps":
       copy..............................
