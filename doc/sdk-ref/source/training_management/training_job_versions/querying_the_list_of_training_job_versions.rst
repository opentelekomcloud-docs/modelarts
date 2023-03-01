:original_name: modelarts_04_0169.html

.. _modelarts_04_0169:

Querying the List of Training Job Versions
==========================================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

::

   from modelarts.session import Session
   from modelarts.estimator import Estimator
   session = Session()
   estimator = Estimator(session, job_id="182626")
   job_version_instance_list = estimator.get_job_version_object_list()

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                                                                                                                                                                                         |
   +===================+===========+========+=====================================================================================================================================================================================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                                                 |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id            | Yes       | String | ID of a training job. You can query **job_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.job_id**, or from the response obtained in :ref:`Querying the List of Training Jobs <modelarts_04_0160>`. |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **get_job_version_object_list** request parameters

   +-----------+-----------+---------+----------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                |
   +===========+===========+=========+============================================================================+
   | is_show   | No        | Boolean | Whether to print the training job version details. Default value: **True** |
   +-----------+-----------+---------+----------------------------------------------------------------------------+

A training object list is returned in the successful response to **get_job_version_object_list**. For details, see :ref:`Table 3 <modelarts_04_0169__en-us_topic_0180515648_en-us_topic_0160436006_table973120224596>`.

.. _modelarts_04_0169__en-us_topic_0180515648_en-us_topic_0160436006_table973120224596:

.. table:: **Table 3** **TrainingJob** object description

   +-------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                                                                                                                                                                                                                       |
   +=============+========+===================================================================================================================================================================================================================================================================================+
   | TrainingJob | Object | Training object. This object contains attributes such as **job_id** and **version_id**, and operations on a training job, such as querying, modifying, or deleting the training job. For example, you can use **job_version_instance.job_id** to obtain the ID of a training job. |
   +-------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
