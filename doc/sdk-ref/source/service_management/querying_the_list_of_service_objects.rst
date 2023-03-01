:original_name: modelarts_04_0206.html

.. _modelarts_04_0206:

Querying the List of Service Objects
====================================

You can use the API to obtain the service object list of a user.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Scenario 1: Query all service objects of a user.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_list_object_resp = Predictor.get_service_object_list(session)

-  Scenario 2: Query a service object based on the search criteria.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_object_list = Predictor.get_service_object_list(session, service_name="digit", order="asc", offset="0", infer_type="real-time")

Parameter Description
---------------------

-  You can use the API to query the service list. The list size is equal to the number of services deployed by the user. Each element in the list is a predictor object. The object attributes are the same as those in service initialization.

   For example, in **service_list_resp = [service_instance1, service_instance2, service_instance3 ...]**, each **service_instance** in the list is a service API that can be called in the service management section.

-  The service list can be queried based on the query parameters. :ref:`Table 1 <modelarts_04_0206__en-us_topic_0180094089_en-us_topic_0160622886_table69015539276>` describes the query parameters.

-  When the model list is queried, details about the services are returned. See :ref:`Table 2 <modelarts_04_0206__en-us_topic_0180094089_en-us_topic_0160622886_table6357123816292>` and :ref:`Table 3 <modelarts_04_0206__en-us_topic_0180094089_en-us_topic_0160622886_table799523318302>`.

.. _modelarts_04_0206__en-us_topic_0180094089_en-us_topic_0160622886_table69015539276:

.. table:: **Table 1** Query parameter description

   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type    | Description                                                                                                                |
   +==============+===========+=========+============================================================================================================================+
   | session      | Yes       | Object  | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.        |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | is_show      | No        | Boolean | Whether to print service object information. Default value: **True**                                                       |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | service_id   | No        | String  | Service ID. By default, the service ID is not filtered.                                                                    |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | service_name | No        | String  | Service name. By default, the service name is not filtered.                                                                |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | infer_type   | No        | String  | Inference mode. The value can be **real-time** or **batch**. By default, this parameter is left blank.                     |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | offset       | No        | Integer | Start page of the paging list. Default value: **0**                                                                        |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | limit        | No        | Integer | Maximum number of records returned on each page. Default value: **1000**                                                   |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | sort_by      | No        | String  | Sorting mode. The value can be **publish_at** or **service_name**. Default value: **publish_at**                           |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | order        | No        | String  | Sorting order. The value can be **asc** or **desc**, indicating the ascending or descending order. Default value: **desc** |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+
   | model_id     | No        | String  | Model ID. By default, the model ID is not filtered.                                                                        |
   +--------------+-----------+---------+----------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_04_0206__en-us_topic_0180094089_en-us_topic_0160622886_table6357123816292:

.. table:: **Table 2** **get_service_list** response parameters

   +-------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type              | Description                                                                                                                          |
   +=============+===================+======================================================================================================================================+
   | total_count | Integer           | Total number of services that meet the search criteria when no paging is implemented                                                 |
   +-------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | count       | Integer           | Number of services in the query result. If **offset** and **limit** are not set, the values of **count** and **total** are the same. |
   +-------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | services    | **service** array | Collection of the queried services                                                                                                   |
   +-------------+-------------------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_04_0206__en-us_topic_0180094089_en-us_topic_0160622886_table799523318302:

.. table:: **Table 3** **service** parameters

   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type    | Description                                                                                                            |
   +==================+=========+========================================================================================================================+
   | service_id       | String  | Service ID                                                                                                             |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | service_name     | String  | Service name                                                                                                           |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | description      | String  | Service description                                                                                                    |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | tenant           | String  | Tenant to whom a service belongs                                                                                       |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | project          | String  | Project to which a service belongs                                                                                     |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | owner            | String  | User to whom a service belongs                                                                                         |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | publish_at       | Number  | Latest service publishing time, in milliseconds calculated from 1970.1.1 0:0:0 UTC                                     |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | infer_type       | String  | Inference mode. The value can be **real-time** or **batch**.                                                           |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | status           | String  | Service status. The value can be **running**, **deploying**, **concerning**, **failed**, **stopped**, or **finished**. |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | progress         | Integer | Deployment progress. This parameter is returned when **status** is **deploying**.                                      |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | invocation_times | Number  | Total number of service calls                                                                                          |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | failed_times     | Number  | Number of failed service calls                                                                                         |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | is_shared        | Boolean | Whether a service is subscribed                                                                                        |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
   | shared_count     | Number  | Number of subscriptions                                                                                                |
   +------------------+---------+------------------------------------------------------------------------------------------------------------------------+
