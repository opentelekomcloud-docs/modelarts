:original_name: modelarts_03_0162.html

.. _modelarts_03_0162:

DevEnviron Permissions
======================

.. table:: **Table 1** Fine-grained permissions for DevEnviron

   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Permission                                                                    | API                                                            | Action                    | IAM Project | Enterprise Project |
   +===============================================================================+================================================================+===========================+=============+====================+
   | Querying the Authentication Information of a Development Environment Instance | GET /v1/{project_id}/demanager/instances/{instance_id}/token   | modelarts:notebook:access | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Creating a Development Environment Instance                                   | POST /v1/{project_id}/demanager/instances                      | modelarts:notebook:create | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying the List of Development Environment Instances                        | GET /v1/{project_id}/demanager/instances                       | modelarts:notebook:list   | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Querying Details About a Development Environment Instance                     | GET /v1/{project_id}/demanager/instances/{instance_id}         | modelarts:notebook:get    | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Modifying the Description of a Development Environment Instance               | PUT /v1/{project_id}/demanager/instances/{instance_id}         | modelarts:notebook:update | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Deleting a Development Environment Instance                                   | DELETE /v1/{project_id}/demanager/instances/{instance_id}      | modelarts:notebook:delete | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
   | Starting or Stopping a Development Environment Instance                       | POST /v1/{project_id}/demanager/instances/{instance_id}/action | modelarts:notebook:action | Y           | Y                  |
   +-------------------------------------------------------------------------------+----------------------------------------------------------------+---------------------------+-------------+--------------------+
