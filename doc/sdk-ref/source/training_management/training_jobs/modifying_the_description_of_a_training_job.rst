:original_name: modelarts_04_0162.html

.. _modelarts_04_0162:

Modifying the Description of a Training Job
===========================================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Modify the description of a training job based on the specified **job_id**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(modelarts_session=session, job_id="182626")
      job_description = estimator.update_job_description(description='update description')

-  Method 2: Modify the description of the training job created in :ref:`Creating a Training Job <modelarts_04_0131>`.

   ::

      job_description = job_instance.update_job_description(description='update description')

-  Method 3: Modify the description of a training job version object returned in :ref:`Querying the List of Training Job Versions <modelarts_04_0169>`.

   ::

      job_description = job_version_instance_list[0].update_job_description(description='update description')

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +-------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                                                                                                                                                              |
   +===================+===========+========+==========================================================================================================================================================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                      |
   +-------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id            | Yes       | String | ID of a training job. Obtain **job_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.job_id**, or from the response in :ref:`Obtaining Training Jobs <modelarts_04_0160>`. |
   +-------------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **update_job_description** request parameters

   +-------------+-----------+--------+------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                    |
   +=============+===========+========+================================================+
   | description | Yes       | String | Description of the training job to be modified |
   +-------------+-----------+--------+------------------------------------------------+

.. table:: **Table 3** **update_job_description** response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================+
   | error_msg             | String                | Error message when the API call fails.                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Error code when the API fails to be called. For details, see `Error Codes <https://docs.otc.t-systems.com/modelarts/api-ref/common_parameters/error_codes.html>`__ in *ModelArts API Reference*. |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_success            | Boolean               | Whether the API call succeeds                                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
