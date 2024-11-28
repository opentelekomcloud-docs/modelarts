:original_name: DeleteImage.html

.. _DeleteImage:

Deleting an Image
=================

Function
--------

Delete an image object. For a private image, you can also delete the image content from SWR using parameters.

Constraints
-----------

None

URI
---

DELETE /v1/{project_id}/images/{id}

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | id         | Yes       | String | Image ID                                                                                 |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID and Name <modelarts_03_0147>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+---------+-------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                           |
   +===========+===========+=========+=======================================================+
   | force     | No        | Boolean | Delete the image content from SWR for private images. |
   +-----------+-----------+---------+-------------------------------------------------------+

Request Parameters
------------------

None

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

.. code-block:: text

   DELETE https://{endpoint}/v1/{project_id}/images/{id}

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "arch" : "x86_64",
     "create_at" : 1671093486722,
     "description" : "",
     "dev_services" : [ "NOTEBOOK", "SSH" ],
     "id" : "c9ab2b2f-edda-4556-bdbb-494e868d043c",
     "name" : "mock-service-python",
     "namespace" : "mock-service1",
     "origin" : "CUSTOMIZE",
     "resource_categories" : [ "CPU" ],
     "service_type" : "UNKNOWN",
     "size" : 387840321,
     "status" : "DELETED",
     "swr_path" : "swr.xxx.com/mock-service1/mock-service-python:0.0.17",
     "tag" : "0.0.17",
     "type" : "DEDICATED",
     "update_at" : 1671093486722,
     "visibility" : "PRIVATE",
     "workspace_id" : "0"
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
204         No Content
401         Unauthorized
403         Forbidden
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
