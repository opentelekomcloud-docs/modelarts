:original_name: modelarts_03_0166.html

.. _modelarts_03_0166:

Workspace Management Permissions
================================

.. table:: **Table 1** Fine-grained permissions for workspace management

   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Permission                         | API                                                   | Action                                                 | Related Action | IAM Project | Enterprise Project |
   +====================================+=======================================================+========================================================+================+=============+====================+
   | Creating a Workspace               | POST /v1/{project_id}/workspaces                      | modelarts:workspace:create                             | N/A            | Y           | Y                  |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Querying the List of Workspaces    | GET /v1/{project_id}/workspaces                       | modelarts:workspace:list                               | N/A            | Y           | Y                  |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Querying Details About a Workspace | GET /v1/{project_id}/workspaces/{ws_id}               | modelarts:workspace:get                                | N/A            | Y           | Y                  |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Modifying a Workspace              | PUT /v1/{project_id}/workspaces/{ws_id}               | modelarts:workspace:update                             | N/A            | Y           | Y                  |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Deleting a Workspace               | DELETE /v1/{project_id}/workspaces/{ws_id}            | modelarts:workspace:delete                             | N/A            | Y           | Y                  |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:service:delete                               |                |             |                    |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:model:delete                                 |                |             |                    |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:tensorboard:delete                           |                |             |                    |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:trainJob:delete                              |                |             |                    |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:exemlProject:deletemodelarts:notebook:delete |                |             |                    |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:dataset:delete                               |                |             |                    |
   |                                    |                                                       |                                                        |                |             |                    |
   |                                    |                                                       | modelarts:notebook:delete                              |                |             |                    |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Querying a Workspace Quota         | GET /v1/{project_id}/workspaces/{workspace_id}/quotas | modelarts:workspace:getQuotas                          | N/A            | Y           | Y                  |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
   | Modifying a Workspace Quota        | PUT /v1/{project_id}/workspaces/{workspace_id}/quotas | modelarts:workspace:updateQuotas                       | N/A            | Y           | Y                  |
   +------------------------------------+-------------------------------------------------------+--------------------------------------------------------+----------------+-------------+--------------------+
