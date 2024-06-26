:original_name: modelarts_03_0365.html

.. _modelarts_03_0365:

DevEnviron Permissions (New Version)
====================================

.. table:: **Table 1** Fine-grained permissions for DevEnviron

   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Permission                                                                        | API                                                                  | Action                                 | IAM Project | Enterprise Project |
   +===================================================================================+======================================================================+========================================+=============+====================+
   | Creating a development environment instance                                       | POST                                                                 | modelarts:notebook:create              | Y           | Y                  |
   |                                                                                   |                                                                      |                                        |             |                    |
   |                                                                                   | /v1/{project_id}/notebooks                                           |                                        |             |                    |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining development environment instances                                       | GET /v1/{project_id}/notebooks                                       | modelarts:notebook:list                | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining details about a development environment instance                        | GET                                                                  | modelarts:notebook:get                 | Y           | Y                  |
   |                                                                                   |                                                                      |                                        |             |                    |
   |                                                                                   | /v1/{project_id}/notebooks/{id}                                      |                                        |             |                    |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Modifying a development environment instance                                      | PUT /v1/{project_id}/notebooks/{id}                                  | modelarts:notebook:update              | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Deleting a development environment instance                                       | DELETE /v1/{project_id}/notebooks/{id}                               | modelarts:notebook:delete              | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Starting a development environment instance of the new version                    | POST /v1/{project_id}/notebooks/{id}/start                           | modelarts:notebook:start               | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Stopping a development environment instance of the new version                    | POST /v1/{project_id}/notebooks/{id}/stop                            | modelarts:notebook:stop                | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining supported images                                                        | GET /v1/{project_id}/images                                          | modelarts:image:list                   | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining details of an image                                                     | GET /v1/{project_id}/images/{id}                                     | modelarts:image:get                    | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining image groups                                                            | GET /v1/{project_id}/images/group                                    | modelarts:image:listGroup              | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Registering a custom image                                                        | POST /v1/{project_id}/images                                         | modelarts:image:register               | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Deleting a custom image                                                           | DELETE /v1/{project_id}/images/{id}                                  | modelarts:image:delete                 | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Saving as a custom image                                                          | POST /v1/{project_id}/notebooks/{id}/create-image                    | modelarts:image:create                 | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining the storage mounted to a development environment instance               | POST /v1/{project_id}/notebooks/{id}/create-image                    | modelarts:notebook:listMountedStorages | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Mounting storage to a development environment instance                            | POST /v1/{project_id}/notebooks/{instance_id}/storage                | modelarts:notebook:mountStorage        | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Obtaining details about the storage mounted to a development environment instance | GET /v1/{project_id}/notebooks/{instance_id}/storage/{storage_id}    | modelarts:notebook:getMountedStorage   | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Unmounting storage from a development environment instance                        | DELETE /v1/{project_id}/notebooks/{instance_id}/storage/{storage_id} | modelarts:notebook:umountStorage       | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
   | Updating the rules for stopping a development environment instance                | PATCH /v1/{project_id}/notebooks/{id}/lease                          | modelarts:notebook:updateStopPolicy    | Y           | Y                  |
   +-----------------------------------------------------------------------------------+----------------------------------------------------------------------+----------------------------------------+-------------+--------------------+
