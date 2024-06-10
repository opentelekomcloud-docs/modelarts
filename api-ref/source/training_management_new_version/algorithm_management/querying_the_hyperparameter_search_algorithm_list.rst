:original_name: ListSearchAlgorithms.html

.. _ListSearchAlgorithms:

Querying the Hyperparameter Search Algorithm List
=================================================

Function
--------

This API is used tp query the hyperparameter search algorithm list.

URI
---

GET /v2/{project_id}/search-algorithms

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                     |
   +============+===========+========+=================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameters

   +-------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter         | Type                                                                                       | Description                                   |
   +===================+============================================================================================+===============================================+
   | search_algo_count | Integer                                                                                    | Number of hyperparameter search algorithms.   |
   +-------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------+
   | search_algo_list  | Array of :ref:`search_algo_list <listsearchalgorithms__response_search_algo_list>` objects | List of all hyperparameter search algorithms. |
   +-------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _listsearchalgorithms__response_search_algo_list:

.. table:: **Table 3** search_algo_list

   +-----------+------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter | Type                                                                   | Description                                         |
   +===========+========================================================================+=====================================================+
   | name      | String                                                                 | Hyperparameter search algorithm name.               |
   +-----------+------------------------------------------------------------------------+-----------------------------------------------------+
   | params    | Array of :ref:`params <listsearchalgorithms__response_params>` objects | List of hyperparameter search algorithm parameters. |
   +-----------+------------------------------------------------------------------------+-----------------------------------------------------+

.. _listsearchalgorithms__response_params:

.. table:: **Table 4** params

   ========= ====== ================================================
   Parameter Type   Description
   ========= ====== ================================================
   key       String Hyperparameter search algorithm parameter name.
   value     String Hyperparameter search algorithm parameter value.
   type      String Hyperparameter search algorithm parameter type.
   ========= ====== ================================================

Example Requests
----------------

The following shows how to query information about the search algorithms supported by coding-free hyperparameter search.

.. code-block:: text

   GET https://endpoint/v2/{project_id}/search-algorithms

Example Responses
-----------------

**Status code: 200**

ok

.. code-block::

   {
     "search_algo_count" : 3,
     "search_algo_list" : [ {
       "name" : "bayes_opt_search",
       "params" : [ {
         "key" : "kind",
         "value" : "ucb",
         "type" : "String"
       }, {
         "key" : "kappa",
         "value" : "2.5",
         "type" : "Float"
       }, {
         "key" : "xi",
         "value" : "0.0",
         "type" : "Float"
       }, {
         "key" : "num_samples",
         "value" : "20",
         "type" : "Integer"
       }, {
         "key" : "seed",
         "value" : "1",
         "type" : "Integer"
       } ],
       "description" : "Hyperparameter search using Gaussian process."
     }, {
       "name" : "tpe_search",
       "params" : [ {
         "key" : "gamma",
         "value" : "0.25",
         "type" : "Float"
       }, {
         "key" : "n_initial_points",
         "value" : "20",
         "type" : "Integer"
       }, {
         "key" : "num_samples",
         "value" : "20",
         "type" : "Integer"
       }, {
         "key" : "seed",
         "value" : "1",
         "type" : "Integer"
       } ],
       "description" : "Hyperparameter search using the tree-structured Parzen estimator algorithm."
     }, {
       "name" : "anneal_search",
       "params" : [ {
         "key" : "avg_best_idx",
         "value" : "2.0",
         "type" : "Float"
       }, {
         "key" : "shrink_coef",
         "value" : "0.1",
         "type" : "Float"
       }, {
         "key" : "num_samples",
         "value" : "20",
         "type" : "Integer"
       }, {
         "key" : "seed",
         "value" : "1",
         "type" : "Integer"
       } ],
       "description" : "Hyperparameter search using simulated annealing algorithm."
     } ]
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
