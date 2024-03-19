:original_name: modelarts_23_0250.html

.. _modelarts_23_0250:

Key Operations Recorded by CTS
==============================

With CTS, you can record operations associated with ModelArts for later query, audit, and backtrack operations.

Prerequisites
-------------

CTS has been enabled. For details, see `Enabling CTS <https://docs.otc.t-systems.com/en-us/usermanual/cts/en-us_topic_0030598498.html>`__

Key Operations Recorded for Data Management
-------------------------------------------

.. table:: **Table 1** Key operations that can be audited for data management

   +------------------------------------------+---------------+------------------------+
   | Operation                                | Resource Type | Trace Name             |
   +==========================================+===============+========================+
   | Creating a dataset                       | dataset       | createDataset          |
   +------------------------------------------+---------------+------------------------+
   | Deleting a dataset                       | dataset       | deleteDataset          |
   +------------------------------------------+---------------+------------------------+
   | Updating a dataset                       | dataset       | updateDataset          |
   +------------------------------------------+---------------+------------------------+
   | Publishing a version of a dataset        | dataset       | publishDatasetVersion  |
   +------------------------------------------+---------------+------------------------+
   | Deleting a dataset version               | dataset       | deleteDatasetVersion   |
   +------------------------------------------+---------------+------------------------+
   | Synchronizing the data source            | dataset       | syncDataSource         |
   +------------------------------------------+---------------+------------------------+
   | Exporting a dataset                      | dataset       | exportDataFromDataset  |
   +------------------------------------------+---------------+------------------------+
   | Importing samples to a dataset           | dataset       | importSamplesToDataset |
   +------------------------------------------+---------------+------------------------+
   | Creating a dataset label                 | dataset       | createLabel            |
   +------------------------------------------+---------------+------------------------+
   | Updating a dataset label                 | dataset       | updateLabel            |
   +------------------------------------------+---------------+------------------------+
   | Deleting a dataset label                 | dataset       | deleteLabel            |
   +------------------------------------------+---------------+------------------------+
   | Deleting a dataset label and its samples | dataset       | deleteLabelWithSamples |
   +------------------------------------------+---------------+------------------------+
   | Adding samples                           | dataset       | uploadSamples          |
   +------------------------------------------+---------------+------------------------+
   | Deleting samples                         | dataset       | deleteSamples          |
   +------------------------------------------+---------------+------------------------+

Key Operations Recorded for Development Environments
----------------------------------------------------

.. table:: **Table 2** Key operations that can be audited in the development environment

   ============================ ============= ======================
   Operation                    Resource Type Trace Name
   ============================ ============= ======================
   Creating a notebook instance Notebook      create_instance
   Deleting a notebook instance Notebook      delete_instance
   Starting a notebook instance Notebook      change_instance_status
   Stopping a notebook instance Notebook      change_instance_status
   ============================ ============= ======================

Key Operations Recorded for Training Jobs
-----------------------------------------

.. table:: **Table 3** Key operations that can be audited in a training job

   +--------------------------------------------------+-------------------------+---------------------------------+
   | Operation                                        | Resource Type           | Trace Name                      |
   +==================================================+=========================+=================================+
   | Creating a training job                          | ModelArtsTrainJob       | createModelArtsTrainJob         |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Creating a version of a training job             | ModelArtsTrainJob       | createModelArtsTrainVersion     |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Stopping a training job                          | ModelArtsTrainJob       | stopModelArtsTrainVersion       |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Modifying the description of a training job      | ModelArtsTrainJob       | updateModelArtsTrainDesc        |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Deleting a training job version                  | ModelArtsTrainJob       | deleteModelArtsTrainVersion     |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Deleting a training job                          | ModelArtsTrainJob       | deleteModelArtsTrainJob         |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Creating a training job configuration            | ModelArtsTrainConfig    | createModelArtsTrainConfig      |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Modifying a training job configuration           | ModelArtsTrainConfig    | updateModelArtsTrainConfig      |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Deleting a training job configuration            | ModelArtsTrainConfig    | deleteModelArtsTrainConfig      |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Creating a visualization job                     | ModelArtsTensorboardJob | createModelArtsTensorboardJob   |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Deleting a visualization job                     | ModelArtsTensorboardJob | deleteModelArtsTensorboardJob   |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Modifying the description of a visualization job | ModelArtsTensorboardJob | updateModelArtsTensorboardDesc  |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Stopping a visualization job                     | ModelArtsTensorboardJob | stopModelArtsTensorboardJob     |
   +--------------------------------------------------+-------------------------+---------------------------------+
   | Restarting a visualization job                   | ModelArtsTensorboardJob | restartModelArtsgTensorboardJob |
   +--------------------------------------------------+-------------------------+---------------------------------+

Key Operations Recorded for AI Application Management
-----------------------------------------------------

.. table:: **Table 4** Key operations that can be audited for AI application management

   ================================ ============= =============
   Operation                        Resource Type Trace Name
   ================================ ============= =============
   Creating an AI application       model         addModel
   Updating an AI application       model         updateModel
   Deleting an AI application       model         deleteModel
   Adding a model conversion task   convert       addConvert
   Updating a model conversion task convert       updateConvert
   Deleting a model conversion task convert       deleteConvert
   ================================ ============= =============

Key Operations Recorded for Service Management
----------------------------------------------

.. table:: **Table 5** Key operations that can be audited for service management

   +------------------------------------------------------------+---------------+---------------------+
   | Operation                                                  | Resource Type | Trace Name          |
   +============================================================+===============+=====================+
   | Deploying a model as a service                             | service       | addService          |
   +------------------------------------------------------------+---------------+---------------------+
   | Deleting a service                                         | service       | deleteService       |
   +------------------------------------------------------------+---------------+---------------------+
   | Updating a service                                         | service       | updateService       |
   +------------------------------------------------------------+---------------+---------------------+
   | Starting/stopping a service                                | service       | startOrStopService  |
   +------------------------------------------------------------+---------------+---------------------+
   | Adding an access key                                       | service       | addAkSk             |
   +------------------------------------------------------------+---------------+---------------------+
   | Deleting an access key                                     | service       | deleteAkSk          |
   +------------------------------------------------------------+---------------+---------------------+
   | Creating a dedicated resource pool                         | cluster       | createCluster       |
   +------------------------------------------------------------+---------------+---------------------+
   | Deleting a dedicated resource pool                         | cluster       | deleteCluster       |
   +------------------------------------------------------------+---------------+---------------------+
   | Adding a node to a dedicated resource pool                 | cluster       | addClusterNode      |
   +------------------------------------------------------------+---------------+---------------------+
   | Deleting a node from a dedicated resource pool             | cluster       | deleteClusterNode   |
   +------------------------------------------------------------+---------------+---------------------+
   | Getting a result from the dedicated resource pool creation | cluster       | createClusterResult |
   +------------------------------------------------------------+---------------+---------------------+
