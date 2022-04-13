.. _modelarts_05_0032:

Error Message "No such file or directory" Displayed in Training Job Logs
========================================================================

Issue Analysis
--------------

When you use ModelArts, your data is stored in the OBS bucket. The data has a corresponding OBS path, for example, **bucket_name/dir/image.jpg**. ModelArts training jobs run in containers, and if they need to access OBS data, they need to know what path to access it from. If ModelArts cannot find the configured path, it is possible that the selected data storage path was configured incorrectly when the training job was created or that the OBS path in the code file is incorrect.

Solution
--------

#. Confirm that the OBS path in the log exists.

   Locate the incorrect OBS path in the log, for example, **obs-test/ModelArts/examples/**. There are two methods to check whether it exists.

   -  On OBS Console, check whether the OBS path exists.

      Log in to OBS console using the current account, and check whether the OBS buckets, folders, and files exist in the OBS path displayed in the log. For example, you can confirm that a given bucket is there and then check if that bucket contains the folder you are looking for based on the configured path.

      -  If the file path exists, go to :ref:`2 <modelarts_05_0032__en-us_topic_0000001096606439_en-us_topic_0285164857_en-us_topic_0166743701_li77081222112915>`.
      -  If it does not exist, change the path configured for the training job to an OBS bucket path that is actually there.

   -  Create a notebook instance, and use an API to check whether the directory exists. In an existing notebook instance or after creating a new notebook instance, run the following command to check whether the directory exists:

      .. code-block::

         import moxing as mox
         mox.file.exists('obs://obs-test/ModelArts/examples/')

      -  If it exists, go to :ref:`2 <modelarts_05_0032__en-us_topic_0000001096606439_en-us_topic_0285164857_en-us_topic_0166743701_li77081222112915>`.
      -  If it does not exist, change it to an available OBS bucket path in the training job.

#. .. _modelarts_05_0032__en-us_topic_0000001096606439_en-us_topic_0285164857_en-us_topic_0166743701_li77081222112915:

   After confirming that the path exists, check whether OBS and ModelArts are in the same region and whether the OBS bucket belongs to another account.

   Log in to the ModelArts console and view the region where ModelArts resides. Log in to the OBS console and view the region where the OBS bucket resides. Check whether they reside in the same region and whether the OBS bucket belongs to another account.

   -  If they are in the same region and the OBS bucket does not belong to another account, go to :ref:`3 <modelarts_05_0032__en-us_topic_0000001096606439_en-us_topic_0285164857_en-us_topic_0166743701_li166204369185>`.
   -  If they are not in the same region or the OBS bucket belongs to another account, create a bucket and a folder in OBS that is in the same region as ModelArts using the same account, and upload data to the bucket.

#. .. _modelarts_05_0032__en-us_topic_0000001096606439_en-us_topic_0285164857_en-us_topic_0166743701_li166204369185:

   In the script of the training job, check whether the API for reading the OBS path in the code file is correct.
