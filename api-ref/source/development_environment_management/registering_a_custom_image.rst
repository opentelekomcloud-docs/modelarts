:original_name: RegisterImage.html

.. _RegisterImage:

Registering a Custom Image
==========================

Function
--------

Register a custom image with ModelArts Image Management.

Constraints
-----------

None

URI
---

POST /v1/{project_id}/images

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type             | Description                                                                                                                     |
   +===================+=================+==================+=================================================================================================================================+
   | arch              | No              | String           | Processor architecture supported by the image. The default value is **X86_64**. Enums:                                          |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **X86_64**: x86 architecture                                                                                                 |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **AARCH64**: Arm architecture                                                                                                |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | description       | No              | String           | Image description with a maximum of 512 characters.                                                                             |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | origin            | No              | String           | Image source, which defaults to **CUSTOMIZE**. This parameter is optional. Enums:                                               |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **CUSTOMIZE**: custom image                                                                                                  |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **IMAGE_SAVE**: image saved by a notebook instance                                                                           |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | resource_category | No              | Array of strings | Flavor supported by the image. The default value is **CPU** or **GPU**. Enums:                                                  |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **CPU**                                                                                                                      |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **GPU**                                                                                                                      |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | service_type      | No              | String           | Supported image types. Options:                                                                                                 |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **COMMON**: common image                                                                                                     |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **INFERENCE**: image used for inference                                                                                      |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  TRAIN: image used for training                                                                                               |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  DEV: image used for development and debugging                                                                                |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  UNKNOWN: image whose supported services are not specified                                                                    |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | services          | No              | Array of strings | Services supported by the image. The default value is **NOTEBOOK** or **SSH**. Enums:                                           |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **NOTEBOOK**: You can access a notebook instance using HTTPS.                                                                |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  **SSH**: You can remotely access a notebook instance from a local IDE through SSH.                                           |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | swr_path          | Yes             | String           | SWR image address                                                                                                               |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | visibility        | No              | String           | Image visibility. The default value is PRIVATE. Options:                                                                        |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  PRIVATE: private image.                                                                                                      |
   |                   |                 |                  |                                                                                                                                 |
   |                   |                 |                  | -  PUBLIC: All users can perform read-only operations based on the image ID.                                                    |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id      | No              | String           | Workspace ID If no workspace is created, the default value is 0. If a workspace is created and used, the actual value prevails. |
   +-------------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                                                                                                                     |
   +========================+=======================+=================================================================================================================================================================================================================+
   | arch                   | String                | Processor architecture supported by the image. Enums:                                                                                                                                                           |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **X86_64**: x86 architecture                                                                                                                                                                                 |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **AARCH64**: Arm architecture                                                                                                                                                                                |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_at              | Long                  | Specifies the time (UTC ms) when the image is created.                                                                                                                                                          |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description            | String                | Image description with a maximum of 512 characters                                                                                                                                                              |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dev_services           | Array of strings      | Services supported by the image. Enums:                                                                                                                                                                         |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **NOTEBOOK**: You can access a notebook instance using HTTPS.                                                                                                                                                |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **SSH**: You can remotely access a notebook instance from a local IDE through SSH.                                                                                                                           |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                     | String                | Specifies the image ID of the notebook instance to be created. The image ID is in the Universally Unique Identifier (UUID) format. For details about how to obtain the ID of a preset image, see ListImage.xml. |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Image name, which contains a maximum of 512 characters, including lowercase letters, digits, hyphens (-), underscores (_), and periods (.)                                                                      |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | namespace              | String                | Organization to which the image belongs. You can create and view the organization on the **Organization Management** page of the SWR console.                                                                   |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | origin                 | String                | Image source, which defaults to **CUSTOMIZE**. This parameter is optional. Enums:                                                                                                                               |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **CUSTOMIZE**: custom image                                                                                                                                                                                  |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **IMAGE_SAVE**: image saved by a notebook instance                                                                                                                                                           |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_categories    | Array of strings      | Flavors supported by the image. Enums:                                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **CPU**                                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **GPU**                                                                                                                                                                                                      |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | service_type           | String                | Supported image types. Options:                                                                                                                                                                                 |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **COMMON**: common image                                                                                                                                                                                     |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **INFERENCE**: image used for inference                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  TRAIN: image used for training                                                                                                                                                                               |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  DEV: image used for development and debugging                                                                                                                                                                |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  UNKNOWN: image whose supported services are not specified                                                                                                                                                    |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                   | Long                  | Specifies the image size, in KB.                                                                                                                                                                                |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                 | String                | Image status. Options:                                                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **INIT**: The image is being initialized.                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **CREATING**: The image is being saved. In this case, the notebook instance is unavailable.                                                                                                                  |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **CREATE_FAILED**: Saving the image failed.                                                                                                                                                                  |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **ERROR**: An error occurs.                                                                                                                                                                                  |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **DELETED**: The image has been deleted.                                                                                                                                                                     |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **ACTIVE**: The image has been saved, which you can view on the SWR console and use to create notebook instances.                                                                                            |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status_message         | String                | Build information during image saving                                                                                                                                                                           |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | support_res_categories | Array of strings      | Flavors supported by the image. Enums:                                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **CPU**                                                                                                                                                                                                      |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **GPU**                                                                                                                                                                                                      |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | swr_path               | String                | SWR image address                                                                                                                                                                                               |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag                    | String                | Image tag                                                                                                                                                                                                       |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                   | String                | Image type. Enums:                                                                                                                                                                                              |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **BUILD_IN**: built-in system image                                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **DEDICATED**: image you have saved                                                                                                                                                                          |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_at              | Long                  | Specifies the time (UTC ms) when the image was last updated.                                                                                                                                                    |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | visibility             | String                | Image visibility. Enums:                                                                                                                                                                                        |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **PRIVATE**: private image                                                                                                                                                                                   |
   |                        |                       |                                                                                                                                                                                                                 |
   |                        |                       | -  **PUBLIC**: All users can perform read-only operations based on the image ID.                                                                                                                                |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id           | String                | Workspace ID. If no workspaces are available, the default value is **0**.                                                                                                                                       |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

The following is an example of how to register a custom image whose resource type is **CPU** and architecture is **X86_64**.

.. code-block::

   {
     "description" : "",
     "resource_category" : [ "CPU" ],
     "arch" : "X86_64",
     "swr_path" : "swr.xxx.com/op_svc_modelarts_container2/pytorch_1_8:train-pytorch_1.8.0-cuda_10.2-py_3.7"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "arch" : "x86_64",
     "create_at" : 1671708630448,
     "description" : "",
     "dev_services" : [ "NOTEBOOK", "SSH" ],
     "id" : "708ca95d-c601-4dc7-86b9-670adfd5e818",
     "name" : "pytorch_1_8",
     "namespace" : "op_svc_modelarts_container2",
     "origin" : "CUSTOMIZE",
     "resource_categories" : [ "CPU" ],
     "service_type" : "UNKNOWN",
     "size" : 3376133259,
     "status" : "ACTIVE",
     "swr_path" : "swr.xxx.com/op_svc_modelarts_container2/pytorch_1_8:train-pytorch_1.8.0-cuda_10.2-py_3.7",
     "tag" : "train-pytorch_1.8.0-cuda_10.2-py_3.7",
     "type" : "DEDICATED",
     "update_at" : 1671708630448,
     "visibility" : "PRIVATE",
     "workspace_id" : "0"
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
201         Created
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
