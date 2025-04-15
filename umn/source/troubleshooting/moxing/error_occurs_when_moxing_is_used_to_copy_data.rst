:original_name: modelarts_13_0036.html

.. _modelarts_13_0036:

Error Occurs When MoXing Is Used to Copy Data
=============================================

Symptom
-------

#. Call **moxing.file.copy_parallel()** to copy a file from the development environment to a bucket. However, the target file does not appear in the bucket.
#. An error occurs when MoXing is used to copy data. Example:

   -  The following error occurs when MoXing is used to copy OBS data in the ModelArts development environment: **keyError: 'request-id'**

   -  The following error occurs when ModelArts uses MoXing to copy data: **No files to copy**

   -  socket.gaierror: [Errno -2] Name or service not known

   -  ERROR:root:Failed to call:

      func=<bound method ObsClient.getObject of <obs.client.ObsClient object at 0x7fd705939710>>

      args=('bucket', 'data/TFRecord/HY_all_inside/no_adjust_light_3/09_06_6x128x128_0000000212.tfrecord')

#. When MoXing is used to copy data, an error message is displayed, indicating that the operation timed out. Example:

   -  TimeoutError: [Errno 110] Connection timed out
   -  WARNING:root:Retry=9,Wait=0.1, Timestamp = 1567152567.5327423

Possible Cause
--------------

The possible causes are as follows:

-  The source file does not exist.
-  The two OBS paths where data is copied are incorrect or are not in the same region.
-  Space of the training job is insufficient.

Solution
--------

Check the following items based on the error message:

#. Check whether the first parameter of **moxing.file.copy_parallel()** contains a file. If it contains no file, the error message "No files to copy" is displayed.

   -  If the file exists, go to :ref:`2 <en-us_topic_0000002268738661__li10628123201314>`.
   -  If the file does not exist, ignore the error and proceed with subsequent operations.

#. .. _en-us_topic_0000002268738661__li10628123201314:

   Check whether the OBS path where data is copied is in the same region as the development environment or training job.

   Log in to the ModelArts management console, and view the region where ModelArts resides. Log in to OBS Console, and view the region where the OBS bucket resides. Check whether they are in the same region.

   -  If they are in the same region, go to step :ref:`3 <en-us_topic_0000002268738661__li2353181314015>`.
   -  If they are not in the same region, create a bucket and a folder in OBS that is in the same region as ModelArts, and upload data to the bucket.

#. .. _en-us_topic_0000002268738661__li2353181314015:

   Check whether the OBS path is **obs://xxx**. You can check whether the OBS path exists as follows:

   **mox.file.exists('obs://bucket_name/sub_dir_0/sub_dir_1')**

   -  If the path exists, go to :ref:`4 <en-us_topic_0000002268738661__li4818125404115>`.
   -  If the path does not exist, change it to an available OBS path.

#. .. _en-us_topic_0000002268738661__li4818125404115:

   Check whether the used resource is a CPU. The **/cache** directory of the CPU and the code directory share 10 GB. The possible cause is insufficient space. You can run the following command in code to check the disk size:

   **os.system('df -hT')**

   -  If disk space is sufficient, go to :ref:`5 <en-us_topic_0000002268738661__li16822185814207>`.
   -  If disk space is insufficient, use GPU resources.

#. .. _en-us_topic_0000002268738661__li16822185814207:

   If data fails to be copied using MoXing in a notebook instance, run the **df -hT** command on the **Terminal** page to check the space size and check whether the failure cause is insufficient space. You can use EVS to attach disks when creating a notebook instance.

If code is correct but the problem persists, submit a service ticket to get professional technical support.
