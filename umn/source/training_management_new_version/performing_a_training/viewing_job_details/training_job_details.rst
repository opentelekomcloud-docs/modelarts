:original_name: modelarts_23_0400.html

.. _modelarts_23_0400:

Training Job Details
====================

#. Log in to the ModelArts management console. In the left navigation pane, choose **Training Management** > **Training Jobs (New)**. The training job list is displayed by default.
#. Click the name of the target training job to view its details.
#. On the left of the training job details page, view basic job settings and algorithm parameters.

   a. Basic job settings

      .. table:: **Table 1** Basic parameters

         =========== =====================================
         Parameter   Description
         =========== =====================================
         Job ID      Unique ID of a training job
         Status      Training job status
         Created     Time when the training job is created
         Duration    Running duration of a training job
         Description Description of a training job
         =========== =====================================

   b. Algorithm parameters

      .. table:: **Table 2** Algorithm parameters

         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                             | Description                                                                                                                                                             |
         +=======================================+=========================================================================================================================================================================+
         | Name                                  | Algorithm used in a training job                                                                                                                                        |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | AI Engine                             | AI engine used in a training job                                                                                                                                        |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Code Directory                        | Code directory where a training job script is stored. If the algorithm is subscribed from AI Gallery, this parameter is unavailable.                                    |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Boot File                             | Location where a boot file is stored. If the algorithm is subscribed from AI Gallery, this parameter is unavailable.                                                    |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Compute Nodes                         | Number of compute nodes                                                                                                                                                 |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Specifications                        | Training specifications used in a training job                                                                                                                          |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Job Log Path                          | Output path of training job logs                                                                                                                                        |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Input Path                            | OBS path where the input data is stored                                                                                                                                 |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter Name                        | Algorithm code parameter specified by the input path                                                                                                                    |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Local Path (Training Parameter Value) | Path for storing the input data in the ModelArts backend container. After the training is started, ModelArts downloads the data stored in OBS to the backend container. |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Output Path                           | OBS path where the output data is stored                                                                                                                                |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter Name                        | Algorithm code parameter specified by the output path                                                                                                                   |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Local Path (Training Parameter Value) | Path for storing the output data in the ModelArts backend container                                                                                                     |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Hyperparameter                        | Hyperparameters used in a training job                                                                                                                                  |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Environment Variable                  | Environment variables for a training job                                                                                                                                |
         +---------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
