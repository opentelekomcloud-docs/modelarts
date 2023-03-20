:original_name: modelarts_04_0185.html

.. _modelarts_04_0185:

Modifying the Description of a Visualization Job
================================================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Modify the description of a visualization job based on the specified **visualization_id**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import VisualizationJob
      session = Session()
      job = VisualizationJob(modelarts_session=session, visualization_id='8992')
      job_description = job.update_visualization_job(job_desc='update visualization job')

-  Method 2: Modify the description of the visualization job created in :ref:`Creating a Visualization Job <modelarts_04_0181>`.

   ::

      job_description = job_visualization_instance.update_visualization_job(job_desc='update visualization job')

-  Method 3: Modify the description of a visualization job object returned in :ref:`Querying the List of Visualization Job Objects <modelarts_04_0182>`.

   ::

      job_description = job_visualization_instance_list[0].update_visualization_job(job_desc='update visualization job')

Parameter Description
---------------------

.. table:: **Table 1** **VisualizationJob** request parameters

   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                         |
   +===================+===========+========+=====================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`. |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | visualization_id  | Yes       | String | ID of a visualization job                                                                                           |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **update_visualization_job** request parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                     |
   +===========+===========+========+=================================================================================+
   | job_desc  | Yes       | String | Description of a visualization job. The value must contain 0 to 256 characters. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------+

.. table:: **Table 3** **update_visualization_job** response parameters

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
