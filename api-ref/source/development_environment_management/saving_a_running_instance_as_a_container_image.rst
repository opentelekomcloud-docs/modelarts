:original_name: CreateImage.html

.. _CreateImage:

Saving a Running Instance as a Container Image
==============================================

Function
--------

A running instance can be saved as a container image. In the saved image, the installed dependency package (pip package) is not lost. In the VS Code remote development scenario, the plug-ins installed on the server are not lost.

Constraints
-----------

None

URI
---

POST /v1/{project_id}/notebooks/{id}/create-image

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | id         | Yes       | String | Notebook instance ID.                                                                    |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                   |
   +==============+===========+========+===============================================================================================================================================+
   | description  | No        | String | Image description with a maximum of 512 characters                                                                                            |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | name         | No        | String | Image name, which contains a maximum of 512 characters, including lowercase letters, digits, hyphens (-), underscores (_), and periods (.)    |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | namespace    | No        | String | Organization to which the image belongs. You can create and view the organization on the **Organization Management** page of the SWR console. |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | tag          | No        | String | Image tag, which contains a maximum of 64 characters, including letters, digits, hyphens (-), underscores (_), and period (.)                 |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id | No        | String | Workspace ID. If no workspaces are available, the default value is **0**.                                                                     |
   +--------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                                                                                   |
   +========================+=======================+===============================================================================================================================================================================+
   | arch                   | String                | Processor architecture supported by the image. Options:                                                                                                                       |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **X86_64**: x86 architecture                                                                                                                                               |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **AARCH64**: Arm architecture                                                                                                                                              |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_at              | Long                  | Specifies the time (UTC ms) when the image is created.                                                                                                                        |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description            | String                | Image description with a maximum of 512 characters                                                                                                                            |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dev_services           | Array of strings      | Services supported by the image. Options:                                                                                                                                     |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **NOTEBOOK**: You can access the notebook instance using HTTPS.                                                                                                            |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **SSH**: You can remotely access the notebook instance from a local IDE through SSH.                                                                                       |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                     | String                | ID of the image used for creating notebook instances. The ID is in Universally Unique Identifier (UUID) format.For details, see :ref:`Querying Supported Images <listimage>`. |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Image name, which contains a maximum of 512 characters, including lowercase letters, digits, hyphens (-), underscores (_), and periods (.)                                    |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | namespace              | String                | Organization to which the image belongs. You can create and view the organization on the **Organization Management** page of the SWR console.                                 |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | origin                 | String                | Image source, which defaults to **CUSTOMIZE**. Options:                                                                                                                       |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **CUSTOMIZE**: user-defined image                                                                                                                                          |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **IMAGE_SAVE**: image saved using a development environment instance                                                                                                       |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource_categories    | Array of strings      | Flavors supported by the image. Options:                                                                                                                                      |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **CPU**                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **GPU**                                                                                                                                                                    |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | service_type           | String                | Supported image types. Options:                                                                                                                                               |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **COMMON**: common image                                                                                                                                                   |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **INFERENCE**: image used for inference                                                                                                                                    |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  TRAIN: image used for training                                                                                                                                             |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  DEV: image used for development and debugging                                                                                                                              |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  UNKNOWN: image whose supported services are not specified                                                                                                                  |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                   | Long                  | Specifies the image size, in KB.                                                                                                                                              |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                 | String                | Image status. Options:                                                                                                                                                        |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **INIT**: The image is being initialized.                                                                                                                                  |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **CREATING**: The image is being saved. In this case, the notebook instance is unavailable.                                                                                |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **CREATE_FAILED**: Saving the image failed.                                                                                                                                |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **ERROR**: An error occurs.                                                                                                                                                |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **DELETED**: The image has been deleted.                                                                                                                                   |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **ACTIVE**: The image has been saved, which you can view on the SWR console and use to create notebook instances.                                                          |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status_message         | String                | Build information during image saving                                                                                                                                         |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | support_res_categories | Array of strings      | Flavors supported by the image. Options:                                                                                                                                      |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **CPU**                                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **GPU**                                                                                                                                                                    |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | swr_path               | String                | SWR image address                                                                                                                                                             |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tag                    | String                | Image tag                                                                                                                                                                     |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                   | String                | Image type. Options:                                                                                                                                                          |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **BUILD_IN**: built-in system image                                                                                                                                        |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **DEDICATED**: private image                                                                                                                                               |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_at              | Long                  | Specifies the time (UTC ms) when the image was last updated.                                                                                                                  |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | visibility             | String                | Image visibility. Options:                                                                                                                                                    |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **PRIVATE**: private image                                                                                                                                                 |
   |                        |                       |                                                                                                                                                                               |
   |                        |                       | -  **PUBLIC**: All users can perform read-only operations based on the image ID.                                                                                              |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | workspace_id           | String                | Workspace ID. If no workspaces are available, the default value is **0**.                                                                                                     |
   +------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

The following is an example of how to save a running instance as a container image whose image name is **pytorch1_4** and organization is **atelier-auto**.

.. code-block::

   {
     "name" : "pytorch1_4",
     "namespace" : "atelier-auto",
     "tag" : "20221223",
     "description" : "save from notebook-x21d",
     "workspace_id" : "0"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "arch" : "x86_64",
     "create_at" : 1671786468811,
     "description" : "notebook2.0 20200816",
     "dev_services" : [ "SSH", "NOTEBOOK" ],
     "id" : "4e0d1854-63e5-4517-b683-a0ee97a692a1",
     "name" : "pytorch1_4",
     "namespace" : "atelier-auto",
     "origin" : "IMAGE_SAVE",
     "resource_categories" : [ "CPU", "GPU" ],
     "service_type" : "TRAIN",
     "status" : "INIT",
     "swr_path" : "swr.xxxxx.com/atelier-auto/pytorch1_4:20221223",
     "tag" : "20221223",
     "type" : "DEDICATED",
     "update_at" : 1671786468811,
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
