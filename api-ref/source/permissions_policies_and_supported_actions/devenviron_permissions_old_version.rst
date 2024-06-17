:original_name: modelarts_03_0162.html

.. _modelarts_03_0162:

DevEnviron Permissions (Old Version)
====================================

.. table:: **Table 1** Fine-grained permissions for DevEnviron

   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Permission                                                 | API                                                            | Action                    | IAM Project | Enterprise Project |
   +============================================================+================================================================+===========================+=============+====================+
   | Creating a development environment instance                | POST /v1/{project_id}/demanager/instances                      | modelarts:notebook:create | Y           | Y                  |
   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Obtaining development environment instances                | GET /v1/{project_id}/demanager/instances                       | modelarts:notebook:list   | Y           | Y                  |
   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Obtaining details about a development environment instance | GET /v1/{project_id}/demanager/instances/{instance_id}         | modelarts:notebook:get    | Y           | Y                  |
   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Modifying a development environment instance               | PUT /v1/{project_id}/demanager/instances/{instance_id}         | modelarts:notebook:update | Y           | Y                  |
   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a development environment instance                | DELETE /v1/{project_id}/demanager/instances/{instance_id}      | modelarts:notebook:delete | Y           | Y                  |
   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Starting or stopping a development environment instance    | POST /v1/{project_id}/demanager/instances/{instance_id}/action | modelarts:notebook:action | Y           | Y                  |
   +------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
