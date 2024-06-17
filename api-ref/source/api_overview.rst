:original_name: modelarts_03_0002.html

.. _modelarts_03_0002:

API Overview
============

All ModelArts APIs are proprietary.

You can use these APIs to manage datasets, training jobs, models, and services.

Data Management APIs
--------------------

.. table:: **Table 1** Dataset management APIs

   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                  | Description                                                                                                                                                                                             |
   +======================================================================+=========================================================================================================================================================================================================+
   | :ref:`Querying the Dataset List <listdatasets>`                      | Query created datasets by page based on specified conditions.                                                                                                                                           |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Dataset <createdataset>`                            | Create a new dataset and determine whether to enable team labeling.                                                                                                                                     |
   |                                                                      |                                                                                                                                                                                                         |
   |                                                                      | -  Enable team labeling. The subsequent operations vary depending on the specified role.                                                                                                                |
   |                                                                      |                                                                                                                                                                                                         |
   |                                                                      |    If a team is specified to assign labeling tasks, the team labeling task is started after the dataset is created.                                                                                     |
   |                                                                      |                                                                                                                                                                                                         |
   |                                                                      |    If a task manager is specified to assign labeling tasks, the manager calls the API for :ref:`starting a team labeling task <startworkforcetask>` to assign and start the team labeling tasks.        |
   |                                                                      |                                                                                                                                                                                                         |
   |                                                                      | -  Disable team labeling. To enable team labeling later, call the API for :ref:`creating a team labeling task <createworkforcetask>` to create team labeling tasks for the dataset.                     |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Dataset <descdataset>`                | Query details about a dataset, including the dataset name, type, and version name based on the dataset ID.                                                                                              |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Modifying a Dataset <updatedataset>`                           | Modify basic information about a dataset, such as the dataset name, description, version, or labels.                                                                                                    |
   |                                                                      |                                                                                                                                                                                                         |
   |                                                                      | Modified labels take effect in the entire dataset, including the samples in the dataset.                                                                                                                |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Dataset <deletedataset>`                            | Delete a dataset based on the dataset ID to release resources.                                                                                                                                          |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Dataset Statistics <getdatasetstats>`                 | Query dataset statistics, such as sample statistics, label statistics, or hard examples based on specified conditions.                                                                                  |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Monitoring Data of a Dataset <getdatasetmetrics>` | Query the monitoring data of a dataset within a specified period, such as the number of labeled samples, number of unlabeled samples, and total number of samples at each time point within the period. |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** APIs for managing dataset versions

   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                               | Description                                                                                                                                                          |
   +===================================================================================+======================================================================================================================================================================+
   | :ref:`Querying the Dataset Version List <listdatasetversions>`                    | Query the versions of a dataset based on the dataset ID to learn about the dataset version evolution.                                                                |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Dataset Labeling Version <createdatasetversion>`                 | Publish a modified dataset as a new version. The modification includes labeling samples, adding samples, and deleting samples in the dataset.                        |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Dataset Labeling Version <describedatasetversion>` | Query details about a specified dataset labeling version, including the name, description, number of files, and storage path based on the dataset ID and version ID. |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Dataset Labeling Version <deletedatasetversion>`                 | Delete a dataset version based on the dataset ID and version ID.                                                                                                     |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** APIs for managing samples

   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                        | Description                                                                                                                                       |
   +============================================================================================+===================================================================================================================================================+
   | :ref:`Querying the Sample List <listsamples>`                                              | Query dataset samples by page based on specified conditions.                                                                                      |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Adding Samples in Batches <uploadsamplesjson>`                                       | Add samples to a dataset in batches for data labeling.                                                                                            |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting Samples in Batches <deletesamples>`                                         | Delete unused samples from a dataset in batches.                                                                                                  |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Sample <describesample>`                                    | Query a single sample based on the sample ID, including the sample status and labels.                                                             |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Sample Search Criteria <listsearch>`                                       | Obtain sample search criteria, such as the label list and attribute key-value pairs of the dataset based on the dataset ID.                       |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Sample List of a Team Labeling Task by Page <listworkforcetasksamples>` | Query the samples of a team labeling task on the data labeling platform by page based on the dataset ID and team labeling task ID.                |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Team Labeling Sample <describeworkforcetasksample>`         | Query details about a sample in a team labeling task on the data labeling platform based on the dataset ID, team labeling task ID, and sample ID. |
   +--------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** APIs for managing labels

   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                | Description                                                                                                                                     |
   +====================================================================================+=================================================================================================================================================+
   | :ref:`Querying the Dataset Label List <listlabels>`                                | Query the labels in a specified dataset version.                                                                                                |
   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Dataset Label <createlabels>`                                     | Create labels during dataset labeling. This function is available only in datasets of the text classification and named entity types.           |
   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Modifying Labels in Batches <updatelabels>`                                  | Modify dataset labels in batches. The modification takes effect in the entire dataset, including the samples in the dataset.                    |
   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting Labels in Batches <deletelabels>`                                   | Delete dataset labels in batches and determine whether to delete the samples with the labels.                                                   |
   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating a Label by Label Name <updatelabel>`                                | Modify a label in a dataset based on the label name. The modification takes effect in the entire dataset, including the samples in the dataset. |
   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Label and the Files with This Label Only <deletelabelandsamples>` | Delete a label in a dataset based on the label name and determine whether to delete the samples with the label.                                 |
   +------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 5** APIs for manual labeling

   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                      | Description                                                                                                                                                                                             |
   +==========================================================+=========================================================================================================================================================================================================+
   | :ref:`Updating Sample Labels in Batches <updatesamples>` | Label multiple samples in a dataset in batches.                                                                                                                                                         |
   |                                                          |                                                                                                                                                                                                         |
   |                                                          | -  Label unlabeled samples. You can use an existing label or create a new label.                                                                                                                        |
   |                                                          | -  Add, modify, or delete labels for labeled samples. You can use an existing label or create a new label.                                                                                              |
   |                                                          |                                                                                                                                                                                                         |
   |                                                          | This API uses a new label list to overwrite the original one to update the sample labels. For example, if an empty label list is used to overwrite the original one, all sample labels will be deleted. |
   +----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** APIs for managing labeling tasks

   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                                  | Description                                                                                                                                                                                       |
   +======================================================================================================+===================================================================================================================================================================================================+
   | :ref:`Querying the Team Labeling Task List of a Dataset <listworkforcetasks>`                        | Query the team labeling tasks of a dataset based on the dataset ID.                                                                                                                               |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Team Labeling Task <createworkforcetask>`                                           | Create a team labeling task based on an existing dataset so that multiple members can concurrently label the dataset.                                                                             |
   |                                                                                                      |                                                                                                                                                                                                   |
   |                                                                                                      | -  If a team is specified to assign labeling tasks, the team labeling task is started after the task is created.                                                                                  |
   |                                                                                                      | -  If a task manager is specified to assign labeling tasks, the manager calls the API for :ref:`starting a team labeling task <startworkforcetask>` to assign and start the team labeling tasks.  |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Team Labeling Task <descworkforcetask>`                               | Query details about a team labeling task based on the dataset ID and team labeling task ID, including the task name, data, and team information.                                                  |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Starting a Team Labeling Task <startworkforcetask>`                                            | Assign and start a team labeling task on the data labeling platform based on the dataset ID and team labeling task ID as the team labeling task manager.                                          |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating a Team Labeling Task <updateworkforcetask>`                                           | Update the description, name, and team information of a team labeling task based on the dataset ID and team labeling task ID.                                                                     |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Team Labeling Task <deleteworkforcetask>`                                           | Delete a team labeling task based on the dataset ID and team labeling task ID.                                                                                                                    |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Team Labeling Acceptance Task <startworkforcesamplingtask>`                         | Start an acceptance task for a team labeling task based on the dataset ID and team labeling task ID.                                                                                              |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Report of a Team Labeling Acceptance Task <getworkforcesamplingtask>`             | Query the report and statistics of a team labeling acceptance task based on the dataset ID and team labeling task ID.                                                                             |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating the Status of a Team Labeling Acceptance Task <updateworkforcesamplingtask>`          | Determine the acceptance scope for a team labeling task, including all labeled data, and update the sample data accordingly.                                                                      |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Statistics for a Team Labeling Task <listworkforcetaskstats>`                         | Query statistics for a team labeling task on the data labeling platform, such as the sample statistics, label statistics, and hard example set based on the dataset ID and team labeling task ID. |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Details About the Progress of a Team Labeling Task Member <getworkforcetaskmetrics>` | Query details about the progress of a team labeling task member in a team labeling task based on the dataset ID and team labeling task ID.                                                        |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Team Labeling Task List by a Team Member <listworkertasks>`                       | Obtain all team labeling tasks on the data labeling platform by page as a member in a team labeling task.                                                                                         |
   +------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 7** APIs for managing the team labeling process

   +-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                     | Description                                                                                                                                                                                                |
   +=========================================================================================+============================================================================================================================================================================================================+
   | :ref:`Submitting Sample Review Comments of an Acceptance Task <acceptsamples>`          | During the acceptance of a team labeling task, provide review comments on samples, including the review result and score.                                                                                  |
   +-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Reviewing Team Labeling Results <reviewsamples>`                                  | Review the team labeling task on the data labeling platform based on the dataset ID and team labeling task ID, determine the review result, and provide review comments as the team labeling task manager. |
   +-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating Labels of Team Labeling Samples in Batches <updateworkforcetasksamples>` | Update sample labels on the data labeling platform in batches, including adding, modifying, and deleting the sample labels. Ensure that only the labels in the dataset can be added or modified.           |
   +-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 8** APIs for managing team labeling

   +---------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | API                                                           | Description                                                                                                                  |
   +===============================================================+==============================================================================================================================+
   | :ref:`Querying the Labeling Team List <listworkforces>`       | Query all labeling teams by page.                                                                                            |
   +---------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Labeling Team <createworkforce>`             | Add a labeling team.                                                                                                         |
   +---------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Labeling Team <descworkforce>` | Query details about a labeling team, including the team name, description, and total number of members based on the team ID. |
   +---------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating a Labeling Team <updateworkforce>`             | Update the name and description of a labeling team based on the team ID.                                                     |
   +---------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Labeling Team <deleteworkforce>`             | Delete a labeling team based on the team ID.                                                                                 |
   +---------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 9** APIs for managing team labeling members

   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                    | Description                                                                                                                                    |
   +========================================================================+================================================================================================================================================+
   | :ref:`Sending an Email to Labeling Team Members <sendemails>`          | Send an email to members in a labeling team to notify them of starting the team labeling task after the task is created.                       |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the List of All Labeling Team Members <listallworkers>` | Query all labeling team members by page based on specified conditions.                                                                         |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Members in a Labeling Team <listworkers>`               | Obtain members in a labeling team by page based on the team ID.                                                                                |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Labeling Team Member <createworker>`                  | Add new members to a labeling team.                                                                                                            |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting Labeling Team Members in Batches <batchdeleteworkers>`  | Delete multiple members from a labeling team in batches.                                                                                       |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Labeling Team Member <descworker>`      | Query details about a member in a labeling team, including the member description, email address, and role based on the team ID and member ID. |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating a Labeling Team Member <updateworker>`                  | Update the description and role of a member in a labeling team based on the team ID and member ID.                                             |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Labeling Team Member <deleteworker>`                  | Delete a member from a labeling team based on the team ID and member ID.                                                                       |
   +------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 10** APIs for importing data

   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                  | Description                                                                                                                                 |
   +======================================================================+=============================================================================================================================================+
   | :ref:`Querying the Dataset Import Task List <listimporttasks>`       | Query historical tasks imported to a dataset by page based on the dataset ID.                                                               |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating an Import Task <importtask>`                          | Create a dataset import task to import labels and data (such as manifest files and OBS data) from a storage system to the dataset.          |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Dataset Import Task <descimporttask>` | Query details about a dataset import task based on the dataset ID and task ID to learn about the data source, import mode, and task status. |
   +----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 11** APIs for exporting data

   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                | Description                                                                                                                                       |
   +====================================================================================+===================================================================================================================================================+
   | :ref:`Querying the Dataset Export Task List <getexporttasksstatusofdataset>`       | Query historical tasks exported from a dataset by page based on the dataset ID.                                                                   |
   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Dataset Export Task <exporttask>`                                 | Export certain data as a new dataset or to OBS.                                                                                                   |
   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Status of a Dataset Export Task <getexporttaskstatusofdataset>` | Query details about a dataset export task based on the dataset ID and task ID to learn about the export type, task status, and number of samples. |
   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 12** APIs for synchronizing data

   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | API                                                                                | Description                                                                     |
   +====================================================================================+=================================================================================+
   | :ref:`Synchronizing a Dataset <syncdatasource>`                                    | Synchronize data and labels from the dataset input path to the dataset.         |
   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+
   | :ref:`Querying the Status of a Dataset Synchronization Task <syncdatasourcestate>` | Query the status of a data source synchronization task based on the dataset ID. |
   +------------------------------------------------------------------------------------+---------------------------------------------------------------------------------+

.. table:: **Table 13** Auto labeling task APIs

   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                  | Description                                                                                                                                                                                                                 |
   +======================================================================================+=============================================================================================================================================================================================================================+
   | :ref:`Querying the Auto Labeling Sample List <listautoannotationsamples>`            | Query the to-be-confirmed auto labeling samples in a dataset by page based on the dataset ID.                                                                                                                               |
   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About an Auto Labeling Sample <describeautoannotationsample>` | Query information of a single auto labeling sample based on the dataset ID and sample ID, such as the sample labels, hard example details, and sample type.                                                                 |
   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Auto Labeling Tasks by Page <listtasks>`                              | Query all auto labeling tasks by page based on the dataset ID.                                                                                                                                                              |
   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Starting an Auto Labeling Task <createtask>`                                   | Start an auto labeling task for unlabeled data to quickly label the data. After the auto labeling task is complete, call the API for :ref:`updating sample labels in batches <updatesamples>` to check the labeling result. |
   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Details About an Auto Labeling Task <autoannotationprogress>`        | Obtain details about an auto labeling task based on the dataset ID and task ID to learn about the task configuration, name, and status.                                                                                     |
   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Stopping an Auto Labeling Task <stopautoannotation>`                           | Stop an ongoing auto labeling task based on the dataset ID and task ID.                                                                                                                                                     |
   +--------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 14** Data processing APIs

   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                            | Description                                                                                                                                                          |
   +================================================================================================+======================================================================================================================================================================+
   | :ref:`Querying the Data Processing Task List <listprocessortasks>`                             | Query all data processing tasks by page.                                                                                                                             |
   |                                                                                                |                                                                                                                                                                      |
   |                                                                                                | Data processing extracts valuable data from a large amount of disordered, difficult-to-understand data.                                                              |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Data Processing Task <createprocessortask>`                                   | Create a data processing task.                                                                                                                                       |
   |                                                                                                |                                                                                                                                                                      |
   |                                                                                                | Data processing involves data validation, data cleansing, data selection, and data augmentation.                                                                     |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Algorithms for a Data Processing Type <getprocessortaskitems>`              | Query the algorithms available for a data processing type.                                                                                                           |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Data Processing Task <describeprocessortask>`                   | Query details about a data processing task, including the task description, status, and version based on the task ID.                                                |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating a Data Processing Task <updateprocessortask>`                                   | Update the description of a data processing task based on the task ID.                                                                                               |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Data Processing Task <deleteprocessortask>`                                   | Delete a data processing task based on the task ID.                                                                                                                  |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Versions of a Data Processing Task <listprocessortaskversions>`             | Query the versions of a data processing task by page based on the task ID.                                                                                           |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a Data Processing Task Version <createprocessortaskversion>`                    | Publish a data processing task as a new version after the task parameters are modified.                                                                              |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying Details About a Data Processing Task Version <descprocessortaskversion>`        | Query details about a version of a data processing task, including the version description, task status, and algorithm template based on the task ID and version ID. |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Data Processing Task Version <deleteprocessortaskversion>`                    | Delete a version of a data processing task based on the task ID and version ID.                                                                                      |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Querying the Result of a Data Processing Task Version <listprocessortaskversionresults>` | Query results of a data processing task by page based on the task ID and version ID.                                                                                 |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Stopping a Data Processing Task Version <stopprocessortaskversion>`                      | Stop an ongoing data processing task based on the task ID and version ID.                                                                                            |
   +------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

DevEnviron APIs
---------------

.. table:: **Table 15** DevEnviron APIs (new version)

   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                          | API                                                                                             | Description                                                                                                                                                                                                       |
   +===============================+=================================================================================================+===================================================================================================================================================================================================================+
   | Managing DevEnviron instances | :ref:`Querying Notebook Instances <listnotebooks>`                                              | Query the list of notebook instances meeting search criteria.                                                                                                                                                     |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Creating a Notebook Instance <createnotebook>`                                            | Create a notebook instance based on parameters such as the instance flavor, AI engine, and storage.                                                                                                               |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Querying Details About a Notebook Instance <shownotebook>`                                | Query details about a notebook instance.                                                                                                                                                                          |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Updating a Notebook Instance <updatenotebook>`                                            | Update a notebook instance.                                                                                                                                                                                       |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Deleting a Notebook Instance <deletenotebook>`                                            | Delete the container and all storage resources of a notebook instance.                                                                                                                                            |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Saving a Running Instance as a Container Image <createimage>`                             | Save the running instance as a container image. In the saved image, the installed dependency package (pip package) is retained. In VS Code remote development, the plug-ins installed on the server are retained. |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Obtaining Available Flavors <listflavors>`                                                | Obtain available flavors.                                                                                                                                                                                         |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Obtaining Flavors Available for a Notebook Instance <showswitchableflavors>`              | Obtain the flavors available for a notebook instance.                                                                                                                                                             |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Obtaining the Available Duration of a Running Notebook Instance <showlease>`              | Obtain the available duration of a running notebook instance.                                                                                                                                                     |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Prolonging a Notebook Instance <renewlease>`                                              | Prolong the available duration of a running notebook instance.                                                                                                                                                    |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Starting a Notebook Instance <startnotebook>`                                             | Start a notebook instance.                                                                                                                                                                                        |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Stopping a Notebook Instance <stopnotebook>`                                              | Stop a notebook instance.                                                                                                                                                                                         |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Dynamically mounting OBS      | :ref:`Obtaining the Notebook Instances with OBS Storage Mounted <listattachableobss>`           | Obtain the notebook instances with OBS storage mounted.                                                                                                                                                           |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Dynamically Mounting OBS <attachobs>`                                                     | Dynamically mount OBS to a notebook instance in the running state.                                                                                                                                                |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Obtaining Details About a Notebook Instance with OBS Storage Mounted <showattachableobs>` | Obtain details about a notebook instance with OBS storage mounted.                                                                                                                                                |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Dynamically Unmounting OBS <cancelobs>`                                                   | Dynamically unmount OBS from a notebook instance.                                                                                                                                                                 |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Image management              | :ref:`Obtaining Supported Images <listimage>`                                                   | Obtain all images by page based on specified conditions.                                                                                                                                                          |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Registering a Custom Image <registerimage>`                                               | Register a custom image with ModelArts image management.                                                                                                                                                          |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Obtaining User Image Groups <listimagegroup>`                                             | Obtain the overview of user image information. Image names are used for aggregation.                                                                                                                              |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Obtaining Details About an Image <showimage>`                                             | Obtain details about an image.                                                                                                                                                                                    |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                               | :ref:`Deleting an Image <deleteimage>`                                                          | Delete an image. For a private image, you can also delete its SWR image using parameters.                                                                                                                         |
   +-------------------------------+-------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 16** DevEnviron APIs (old version)

   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | API                                                                                        | Description                                                                 |
   +============================================================================================+=============================================================================+
   | :ref:`Creating a Development Environment Instance <modelarts_03_0110>`                     | Create a development environment instance for code development.             |
   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | :ref:`Obtaining Development Environment Instances <modelarts_03_0111>`                     | Obtain the development environment instances that meet the search criteria. |
   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | :ref:`Obtaining Details About a Development Environment Instance <modelarts_03_0112>`      | Query details about a notebook instance.                                    |
   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | :ref:`Modifying the Description of a Development Environment Instance <modelarts_03_0113>` | Modify the description of a development environment instance.               |
   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | :ref:`Deleting a Development Environment Instance <modelarts_03_0114>`                     | Delete a development environment instance.                                  |
   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+
   | :ref:`Managing a Development Environment Instance <modelarts_03_0115>`                     | Start or stop a development environment instance.                           |
   +--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------+

Training Management APIs
------------------------

.. table:: **Table 17** Algorithm management APIs

   +-------------------------------------------------------------------+---------------------------------------------------------+
   | API                                                               | Description                                             |
   +===================================================================+=========================================================+
   | :ref:`Creating an Algorithm <createalgorithm>`                    | Create an algorithm.                                    |
   +-------------------------------------------------------------------+---------------------------------------------------------+
   | :ref:`Obtaining Algorithms <listalgorithms>`                      | Obtain algorithms.                                      |
   +-------------------------------------------------------------------+---------------------------------------------------------+
   | :ref:`Obtaining Details About an Algorithm <showalgorithmbyuuid>` | Obtain a specified algorithm based on the algorithm ID. |
   +-------------------------------------------------------------------+---------------------------------------------------------+
   | :ref:`Updating an Algorithm <changealgorithm>`                    | Update an algorithm.                                    |
   +-------------------------------------------------------------------+---------------------------------------------------------+
   | :ref:`Deleting an Algorithm <deletealgorithm>`                    | Delete an algorithm.                                    |
   +-------------------------------------------------------------------+---------------------------------------------------------+

.. table:: **Table 18** APIs for managing training jobs

   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | API                                                                                                      | Description                                                                                                   |
   +==========================================================================================================+===============================================================================================================+
   | :ref:`Creating a Training Job <createtrainingjob>`                                                       | Create a training job.                                                                                        |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Details About a Training Job <showtrainingjobdetails>`                                   | Obtain details about a training job.                                                                          |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Modifying the Description of a Training Job <changetrainingjobdescription>`                        | Modify the description of a training job.                                                                     |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Training Job <deletetrainingjob>`                                                       | Delete a training job.                                                                                        |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Terminate a Training Job <stoptrainingjob>`                                                        | Terminate a training job. Only jobs in the creating, awaiting, or running state can be terminated.            |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining the Logs of a Specified Task in a Training Job (Preview) <showtrainingjoblogspreview>`   | Obtain the logs of a specified task in a training job (preview).                                              |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining the Logs of a Specified Task in a Training Job (OBS Link) <showobsurloftrainingjoblogs>` | Obtain the logs of a specified task in a training job (OBS link). You can view all logs or download the logs. |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining the Runtime Metrics of a Specified Task in a Training Job <showtrainingjobmetrics>`      | Obtain the runtime metrics of a specified task in a training job.                                             |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Training Jobs <listtrainingjobs>`                                                        | Obtain the created training jobs by search criteria.                                                          |
   +----------------------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+

.. table:: **Table 19** APIs for resources and engine specifications

   +--------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | API                                                                                              | Description                                                    |
   +==================================================================================================+================================================================+
   | :ref:`Obtaining the General Specifications Supported by a Training Job <showtrainingjobflavors>` | Obtain the general specifications supported by a training job. |
   +--------------------------------------------------------------------------------------------------+----------------------------------------------------------------+
   | :ref:`Obtaining the Preset AI Frameworks Supported by a Training Job <showtrainingjobengines>`   | Obtain the preset AI frameworks supported by a training job.   |
   +--------------------------------------------------------------------------------------------------+----------------------------------------------------------------+

Model Management APIs
---------------------

.. table:: **Table 20** Model management APIs

   +--------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | API                                              | Description                                                                                                 |
   +==================================================+=============================================================================================================+
   | :ref:`Importing a Model <createmodel>`           | Import a model.                                                                                             |
   +--------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Models <listmodels>`             | Obtain the models that meet the search criteria.                                                            |
   +--------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | :ref:`Viewing Details About a Model <showmodel>` | View details about a model based on the model ID.                                                           |
   +--------------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Model <deletemodel>`            | Delete a specified model based on the model ID. All versions of the model can be deleted in cascading mode. |
   +--------------------------------------------------+-------------------------------------------------------------------------------------------------------------+

Service Management APIs
-----------------------

.. table:: **Table 21** Service management APIs

   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | API                                                                                      | Description                                                                                                                   |
   +==========================================================================================+===============================================================================================================================+
   | :ref:`Deploying a Service <createservice>`                                               | Deploy a model service.                                                                                                       |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Services <listservices>`                                                 | Obtain model services.                                                                                                        |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Service Details <showservice>`                                           | Obtain details about a model service based on the service ID.                                                                 |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Updating Service Configurations <updateservice>`                                   | Update a model service.                                                                                                       |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Service Monitoring <showservicemonitorinfo>`                             | Obtain service monitoring information.                                                                                        |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Service Update Logs <showserviceupdatelogs>`                             | Obtain the update logs of a real-time service.                                                                                |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Service Event Logs <showserviceevents>`                                  | Obtain service event logs, including service operation records, key actions during deployment, and deployment failure causes. |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting a Service <deleteservice>`                                                | Delete a model service.                                                                                                       |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Supported Service Deployment Specifications <showservicespecifications>` | Obtain supported service deployment specifications.                                                                           |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Obtaining Dedicated Resource Pools <listclusters>`                                 | Obtain dedicated resource pools.                                                                                              |
   +------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+

Resource Management APIs
------------------------

.. table:: **Table 22** Configuration management APIs

   +-------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+
   | API                                                         | Description                                                                                                      |
   +=============================================================+==================================================================================================================+
   | :ref:`Obtaining OS Configuration Parameters <showosconfig>` | Obtain the configuration parameters of the ModelArts OS service, such as the CIDR block and user resource quota. |
   +-------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 23** Configuration management APIs

   +------------------------------------------+-------------------------------------------------------------------------------------------------------------+
   | API                                      | Description                                                                                                 |
   +==========================================+=============================================================================================================+
   | :ref:`Obtaining OS Quotas <showosquota>` | Obtain the quotas of some ModelArts OS resources, such as the quotas for resource pool quotas and networks. |
   +------------------------------------------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 24** Plug-in template management APIs

   +----------------------------------------------------------+-------------------------------------------------+
   | API                                                      | Description                                     |
   +==========================================================+=================================================+
   | :ref:`Obtaining a Plug-in Template <showplugintemplate>` | Obtain details of a specified plug-in template. |
   +----------------------------------------------------------+-------------------------------------------------+

.. table:: **Table 25** Node management APIs

   +---------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | API                                                     | Description                                                                                                     |
   +=========================================================+=================================================================================================================+
   | :ref:`Obtaining Nodes <listpoolnodes>`                  | Obtain the nodes in a resource pool.                                                                            |
   +---------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting Nodes in Batches <batchdeletepoolnodes>` | Delete nodes from a specific resource pool in batches. At least one node must be reserved in the resource pool. |
   +---------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 26** Event management APIs

   ==================================== ==============
   API                                  Description
   ==================================== ==============
   :ref:`Obtaining Events <listevents>` Obtain events.
   ==================================== ==============

.. table:: **Table 27** Network management APIs

   +----------------------------------------------------+----------------------------------------------------+
   | API                                                | Description                                        |
   +====================================================+====================================================+
   | :ref:`Creating Network Resources <createnetwork>`  | Create network resources.                          |
   +----------------------------------------------------+----------------------------------------------------+
   | :ref:`Obtaining Network Resources <listnetworks>`  | Obtain a list of network resources.                |
   +----------------------------------------------------+----------------------------------------------------+
   | :ref:`Obtaining a Network Resource <shownetwork>`  | Obtain details about a specified network resource. |
   +----------------------------------------------------+----------------------------------------------------+
   | :ref:`Deleting a Network Resource <deletenetwork>` | Delete a specified network resource.               |
   +----------------------------------------------------+----------------------------------------------------+
   | :ref:`Updating a Network Resource <patchnetwork>`  | Update a specified network resource.               |
   +----------------------------------------------------+----------------------------------------------------+

.. table:: **Table 28** Resource metric management APIs

   +------------------------------------------------------------------------+--------------------------------------------------------------------------+
   | API                                                                    | Description                                                              |
   +========================================================================+==========================================================================+
   | :ref:`Obtaining the Real-Time Resource Usage <showpoolruntimemetrics>` | Obtain the real-time usage of all resource pools in the current project. |
   +------------------------------------------------------------------------+--------------------------------------------------------------------------+

.. table:: **Table 29** Resource pool management APIs

   +-----------------------------------------------------------------+-------------------------------------------------------+
   | API                                                             | Description                                           |
   +=================================================================+=======================================================+
   | :ref:`Creating a Resource Pool <createpool>`                    | Create a resource pool.                               |
   +-----------------------------------------------------------------+-------------------------------------------------------+
   | :ref:`Obtaining Resource Pools <listpools>`                     | Obtain resource pools.                                |
   +-----------------------------------------------------------------+-------------------------------------------------------+
   | :ref:`Obtaining a Resource Pool <showpool>`                     | Obtain details about a specified resource pool.       |
   +-----------------------------------------------------------------+-------------------------------------------------------+
   | :ref:`Deleting a Resource Pool <deletepool>`                    | Delete a specified resource pool.                     |
   +-----------------------------------------------------------------+-------------------------------------------------------+
   | :ref:`Updating a Resource Pool <patchpool>`                     | Update a specified resource pool.                     |
   +-----------------------------------------------------------------+-------------------------------------------------------+
   | :ref:`Monitoring a Resource Pool <showpoolmonitor>`             | Obtain the monitoring information of a resource pool. |
   +-----------------------------------------------------------------+-------------------------------------------------------+
   | :ref:`Collecting Resource Pool Statistics <showpoolstatistics>` | Obtain the statistics of a resource pool.             |
   +-----------------------------------------------------------------+-------------------------------------------------------+

.. table:: **Table 30** Resource flavor management APIs

   +---------------------------------------------------------+--------------------------+
   | API                                                     | Description              |
   +=========================================================+==========================+
   | :ref:`Obtaining Resource Flavors <listresourceflavors>` | Obtain resource flavors. |
   +---------------------------------------------------------+--------------------------+

.. table:: **Table 31** APIs for managing resource pool jobs

   +---------------------------------------------------------------------------------------+-----------------------------------------------------+
   | API                                                                                   | Description                                         |
   +=======================================================================================+=====================================================+
   | :ref:`Obtaining Dedicated Resource Pool Jobs <listworkloads>`                         | Obtain dedicated resource pool jobs.                |
   +---------------------------------------------------------------------------------------+-----------------------------------------------------+
   | :ref:`Obtaining Statistics for Dedicated Resource Pool Jobs <showworkloadstatistics>` | Obtain statistics for dedicated resource pool jobs. |
   +---------------------------------------------------------------------------------------+-----------------------------------------------------+

Authorization Management APIs
-----------------------------

.. table:: **Table 32** Authorization management APIs

   +------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | API                                                        | Description                                                                                                                                                                                                             |
   +============================================================+=========================================================================================================================================================================================================================+
   | :ref:`Viewing an Authorization List <getauthorizations>`   | View an authorization list.                                                                                                                                                                                             |
   +------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Configuring Authorization <createauthorization>`     | Configure ModelArts authorization. ModelArts functions such as training management, development environment, data management, and real-time services can be properly used only after required permissions are assigned. |
   +------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Deleting Authorization <deleteauthorizations>`       | Delete the authorization of a specified user or all users.                                                                                                                                                              |
   +------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | :ref:`Creating a ModelArts Agency <createmodelartsagency>` | Create a ModelArts agency for dependent services such as OBS, SWR, and IEF.                                                                                                                                             |
   +------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
