:original_name: modelarts_06_0003.html

.. _modelarts_06_0003:

What Are the Precautions for Switching Training Jobs from the Old Version to the New Version?
=============================================================================================

The differences between the new version and the old version lie in:

-  :ref:`Differences in Training Job Creation <en-us_topic_0000001943979045__section102743424224>`
-  :ref:`Differences in Training Code Adaptation <en-us_topic_0000001943979045__section1159344293111>`
-  :ref:`Differences in Built-in Training Engines <en-us_topic_0000001943979045__section8673132164615>`

.. _en-us_topic_0000001943979045__section102743424224:

Differences in Training Job Creation
------------------------------------

-  In earlier versions, you can create a training job using **Algorithm Management**, **Frequently-used**, and **Custom**.
-  In the new version, you can create a training job using **Custom algorithm**\ or **My algorithm**.

The new version reorganizes the algorithms to help you find them more easily. Existing training jobs are not affected.

-  The saved algorithms in **Algorithm Management** in the old version are in **My algorithm** in the new version.
-  The **Frequently-used** in the old version is the **Custom algorithm** in the new version. Select **Preset image** for **Boot Mode** when you create jobs using the new version.
-  The **Custom** in the old version is the **Custom algorithm** in the new version. Select **Custom image** for **Boot Mode** when you create jobs using the new version.

.. _en-us_topic_0000001943979045__section1159344293111:

Differences in Training Code Adaptation
---------------------------------------

In the old version, you are required to configure data input and output as follows:

.. code-block::

   # Parse CLI parameters.
   import argparse
   parser = argparse.ArgumentParser(description='MindSpore Lenet Example')
   parser.add_argument('--data_url', type=str, default="./Data",
                       help='path where the dataset is saved')
   parser.add_argument('--train_url', type=str, default="./Model", help='if is test, must provide\
                       path where the trained ckpt file')
   args = parser.parse_args()
   ...
   # Download data to your local container. In the code, local_data_path specifies the training input path.
   mox.file.copy_parallel(args.data_url, local_data_path)
   ...
   # Upload the local container data to the OBS path.
   mox.file.copy_parallel(local_output_path, args.train_url)

In the new version, you only need to configure training input and output. In the code, **arg.data_url** and **arg.train_url** are used as local paths. For details, see Developing a Custom Script.

.. code-block::

   # Parse CLI parameters.
   import argparse
   parser = argparse.ArgumentParser(description='MindSpore Lenet Example')
   parser.add_argument('--data_url', type=str, default="./Data",
                       help='path where the dataset is saved')
   parser.add_argument('--train_url', type=str, default="./Model", help='if is test, must provide\
                       path where the trained ckpt file')
   args = parser.parse_args()
   ...
   # The downloaded code does not need to be set. Use data_url and train_url for data training and output.
   # Download data to your local container. In the code, local_data_path specifies the training input path.
   #mox.file.copy_parallel(args.data_url, local_data_path)
   ...
   # Upload the local container data to the OBS path.
   #mox.file.copy_parallel(local_output_path, args.train_url)

.. _en-us_topic_0000001943979045__section8673132164615:

Differences in Built-in Training Engines
----------------------------------------

-  In the new version, MoXing 2.0.0 or later is installed by default for built-in training engines.

-  In the new version, Python 3.7 or later is used for built-in training engines.

-  In the new image, the default home directory has been changed from **/home/work** to **/home/ma-user**. Check whether the training code contains hard coding of **/home/work**.

-  Built-in training engines are different between the old and new versions. Commonly used built-in training engines have been upgraded in the new version.

   To use a training engine in the old version, switch to the old version. :ref:`Table 1 <en-us_topic_0000001943979045__table18869123641314>` lists the differences between the built-in training engines in the old and new versions.

   .. _en-us_topic_0000001943979045__table18869123641314:

   .. table:: **Table 1** Differences between the built-in training engines in the old and new versions

      +-----------------------+--------------------------------------+-------------+-------------+
      | Runtime Environment   | Built-in Training Engine and Version | Old Version | New Version |
      +=======================+======================================+=============+=============+
      | Ascend-Powered-Engine | Mindspore-1.3.0                      | Y           | x           |
      +-----------------------+--------------------------------------+-------------+-------------+
      |                       | Mindspore-1.7.0                      | x           | Y           |
      +-----------------------+--------------------------------------+-------------+-------------+
      |                       | TensorFlow-1.15                      | Y           | Y           |
      +-----------------------+--------------------------------------+-------------+-------------+
