:original_name: modelarts_04_0196.html

.. _modelarts_04_0196:

Obtaining the Model Object List
===============================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  **Scenario 1**: Obtain all model objects of a user.

   ::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_object_list = Model.get_model_object_list(session)

-  **Scenario 2**: Obtain a model object based on the search criteria.

   ::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_object_list = Model.get_model_object_list(session, model_status="published", model_name="digit", order="desc")

Parameters
----------

-  After you obtain a model list, the size of the list is equal to the number of models that have been deployed by the current user. Each element in the list is a model object. The object attributes are the same as those in :ref:`Querying the Details About a Model <modelarts_04_0197>`. For example, in **model_list = [model_instance1, model_instance2, model_instance3 ...]**, each **model_instance** in the list is a model API that can be called.
-  The model list can be obtained based on the query parameters. :ref:`Table 1 <modelarts_04_0196__en-us_topic_0180094082_en-us_topic_0160574220_table2918868102420>` describes the query parameters.
-  When you obtain a model list, details about the models are returned. See :ref:`Table 2 <modelarts_04_0196__en-us_topic_0180094082_en-us_topic_0160574220_table1954662185412>` and :ref:`Table 3 <modelarts_04_0196__en-us_topic_0180094082_en-us_topic_0160574220_table1198992710540>`.
-  A maximum of 150 model objects can be obtained.

.. _modelarts_04_0196__en-us_topic_0180094082_en-us_topic_0160574220_table2918868102420:

.. table:: **Table 1** Query parameters

   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Type    | Description                                                                                                                 |
   +===============+===========+=========+=============================================================================================================================+
   | model_name    | No        | String  | Model name. Fuzzy match is supported.                                                                                       |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | model_version | No        | String  | Model version                                                                                                               |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | model_status  | No        | String  | Model status. The value can be **publishing**, **published**, or **failed**. You can obtain models based on their statuses. |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | description   | No        | String  | Description. Fuzzy match is supported.                                                                                      |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | offset        | No        | Integer | Index of the page to be obtained. Default value: **0**                                                                      |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | limit         | No        | Integer | Maximum number of records returned on each page. Default value: **280**                                                     |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | sort_by       | No        | String  | Sorting mode. The value can be **create_at**, **model_version**, or **model_size**. Default value: **create_at**            |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | order         | No        | String  | Sorting order. The value can be **asc** or **desc**, indicating the ascending or descending order. Default value: **desc**  |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+
   | workspace_id  | No        | String  | Workspace ID. Default value: **0**                                                                                          |
   +---------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_04_0196__en-us_topic_0180094082_en-us_topic_0160574220_table1954662185412:

.. table:: **Table 2** **get_model_list** parameters

   +-------------+-----------------+------------------------------------------------------------------------------------+
   | Parameter   | Type            | Description                                                                        |
   +=============+=================+====================================================================================+
   | total_count | Integer         | Total number of models that meet the search criteria when no paging is implemented |
   +-------------+-----------------+------------------------------------------------------------------------------------+
   | count       | Integer         | Number of models                                                                   |
   +-------------+-----------------+------------------------------------------------------------------------------------+
   | models      | **model** array | Model metadata                                                                     |
   +-------------+-----------------+------------------------------------------------------------------------------------+

.. _modelarts_04_0196__en-us_topic_0180094082_en-us_topic_0160574220_table1198992710540:

.. table:: **Table 3** **model** parameters

   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type   | Description                                                                                                                                       |
   +===============+========+===================================================================================================================================================+
   | model_id      | String | Model ID                                                                                                                                          |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_name    | String | Model name                                                                                                                                        |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_version | String | Model version                                                                                                                                     |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_type    | String | Model type. The value can be **TensorFlow**, **MXNet**, **Spark_MLlib**, **Scikit_Learn**, **XGBoost**, **MindSpore**, **Image**, or **PyTorch**. |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_size    | Long   | Model size, in bytes                                                                                                                              |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant        | String | Tenant to whom a model belongs                                                                                                                    |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | project       | String | Project to which a model belongs                                                                                                                  |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | owner         | String | User to which a model belongs                                                                                                                     |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_at     | Long   | Time when a model is created, in milliseconds calculated from 1970.1.1 0:0:0 UTC                                                                  |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | description   | String | Model description                                                                                                                                 |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_type   | String | Model source type. This parameter is valid only when the model is deployed by an ExeML project. The value is **auto**.                            |
   +---------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------+
