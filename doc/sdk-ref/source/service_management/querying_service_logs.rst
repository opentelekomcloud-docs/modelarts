:original_name: modelarts_04_0209.html

.. _modelarts_04_0209:

Querying Service Logs
=====================

You can use the API to query the logs of a service object.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Query service logs based on the service created in :ref:`Deploying a Real-Time Service <modelarts_04_0201>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_instance = Predictor(session, service_id="input your service_id")
      predictor_log = predictor_instance.get_service_logs()

-  Method 2: Query service logs based on the service object returned in :ref:`Querying the List of Service Objects <modelarts_04_0206>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_object_list = Predictor.get_service_object_list(session)
      predictor_instance = predictor_object_list[0]
      predictor_log = predictor_instance.get_service_logs()

Parameter Description
---------------------

.. table:: **Table 1** **get_service_logs** response parameters

   ============ ============= ===================
   Parameter    Type          Description
   ============ ============= ===================
   service_id   String        Service ID
   service_name String        Service name
   logs         **log** array Service update logs
   ============ ============= ===================

.. table:: **Table 2** **log** parameters

   +-------------+------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                                             |
   +=============+==================+=========================================================================================================+
   | update_time | Long             | Time when a service is updated, in milliseconds calculated from 1970.1.1 0:0:0 UTC                      |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------+
   | result      | String           | Update result. The value can be **SUCCESS**, **FAIL**, or **RUNNING**.                                  |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------+
   | config      | **config** array | Updated service configurations. This parameter is returned when **infer_type** is set to **real-time**. |
   +-------------+------------------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **config** parameters

   +----------------+---------------------+------------------------------------------------------------------+
   | Parameter      | Type                | Description                                                      |
   +================+=====================+==================================================================+
   | model_id       | String              | Model ID                                                         |
   +----------------+---------------------+------------------------------------------------------------------+
   | model_name     | String              | Model name                                                       |
   +----------------+---------------------+------------------------------------------------------------------+
   | model_version  | String              | Model version                                                    |
   +----------------+---------------------+------------------------------------------------------------------+
   | weight         | Integer             | Traffic weight allocated to a model                              |
   +----------------+---------------------+------------------------------------------------------------------+
   | specification  | String              | Resource flavor                                                  |
   +----------------+---------------------+------------------------------------------------------------------+
   | instance_count | Integer             | Number of instances deployed in a model                          |
   +----------------+---------------------+------------------------------------------------------------------+
   | envs           | Map<String, String> | Environment variable key-value pair required for running a model |
   +----------------+---------------------+------------------------------------------------------------------+

.. table:: **Table 4** **result** parameters

   +-----------+---------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                              |
   +===========+=========+==========================================================================================================+
   | node_name | String  | Name of an edge node                                                                                     |
   +-----------+---------+----------------------------------------------------------------------------------------------------------+
   | operation | String  | Operation type. The value can be **deploy** or **delete**.                                               |
   +-----------+---------+----------------------------------------------------------------------------------------------------------+
   | result    | Boolean | Operation result. **true** indicates a successful operation, and **false** indicates a failed operation. |
   +-----------+---------+----------------------------------------------------------------------------------------------------------+
