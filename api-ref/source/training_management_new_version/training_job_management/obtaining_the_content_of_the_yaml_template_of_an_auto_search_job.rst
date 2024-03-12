:original_name: ShowAutoSearchYamlTemplateContent.html

.. _ShowAutoSearchYamlTemplateContent:

Obtaining the Content of the YAML Template of an Auto Search Job
================================================================

Function
--------

This API is used to obtain the content of the YAML template of an auto search job.

URI
---

GET /v2/{project_id}/training-jobs/autosearch/yaml-templates/{algorithm_type}/{algorithm_name}

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                     |
   +================+===========+========+=================================================================================+
   | algorithm_type | Yes       | String | Type of the search algorithm.                                                   |
   +----------------+-----------+--------+---------------------------------------------------------------------------------+
   | algorithm_name | Yes       | String | Name of the search algorithm.                                                   |
   +----------------+-----------+--------+---------------------------------------------------------------------------------+
   | project_id     | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +----------------+-----------+--------+---------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   ========= ====== ==================
   Parameter Type   Description
   ========= ====== ==================
   file_name String YAML file name.
   content   String YAML file content.
   ========= ====== ==================

Example Requests
----------------

The following shows how to query the content of the YAML configuration file whose **algorithm_type** is **hpo** and **algorithm_name** is **Bayes**.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/training-jobs/autosearch/yaml-templates/hpo/Bayes

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "file_name" : "Bayes.yaml",
     "content" : "general:\r\n  instance_per_trial: 1\r\n  gpu_per_instance: 1\r\n  cpu_per_instance: 1\r\n\r\nsearch_space:\r\n  - params:   # only support continuous params\r\n    - type: continuous_param\r\n      name : lr\r\n      start: 0.001\r\n      stop: 0.1\r\n\r\nsearch_algorithm:\r\n  type: bayes_opt_search\r\n  max_concurrent: 4\r\n  reward_attr: accuracy\r\n  num_samples: 8\r\n  kind : ucb\r\n  save_model_count : 3\r\n  mode: max\r\n\r\nscheduler:\r\n  type: FIFOScheduler"
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         ok
=========== ===========

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
