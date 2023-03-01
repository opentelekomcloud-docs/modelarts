:original_name: modelarts_04_0208.html

.. _modelarts_04_0208:

Querying Service Monitoring Details
===================================

You can use the API to query the monitoring information about a service.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Query the monitoring information about the service created in :ref:`Deploying a Real-Time Service <modelarts_04_0201>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_instance = Predictor(session, service_id="input your service_id")
      predictor_monitor = predictor_instance.get_service_monitor()

-  Method 2: Query the monitoring information about the service object returned in :ref:`Querying the List of Service Objects <modelarts_04_0206>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_object_list = Predictor.get_service_object_list(session)
      predictor_instance = predictor_object_list[0]
      predictor_monitor = predictor_instance.get_service_monitor()

Parameter Description
---------------------

.. table:: **Table 1** **get_service_monitor** response parameters

   +--------------+----------------------------------------------------------------+--------------------+
   | Parameter    | Type                                                           | Description        |
   +==============+================================================================+====================+
   | service_id   | String                                                         | Service ID         |
   +--------------+----------------------------------------------------------------+--------------------+
   | service_name | String                                                         | Service name       |
   +--------------+----------------------------------------------------------------+--------------------+
   | monitors     | **monitor** array corresponding to **infer_type** of a service | Monitoring details |
   +--------------+----------------------------------------------------------------+--------------------+

.. table:: **Table 2** **monitor** parameters corresponding to **real-time**

   ================ ======= =====================================
   Parameter        Type    Description
   ================ ======= =====================================
   model_id         String  Model ID
   model_name       String  Model name
   model_version    String  Model version
   invocation_times Number  Total number of model instance calls
   failed_times     Number  Number of failed model instance calls
   cpu_core_usage   Float   Number of used CPUs
   cpu_core_total   Float   Total number of CPUs
   cpu_memory_usage Integer Used memory, in MBs
   cpu_memory_total Integer Total memory, in MBs
   gpu_usage        Float   Number of used GPUs
   gpu_total        Float   Total number of GPUs
   ================ ======= =====================================
