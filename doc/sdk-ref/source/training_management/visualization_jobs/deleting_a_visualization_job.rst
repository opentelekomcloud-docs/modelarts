:original_name: modelarts_04_0188.html

.. _modelarts_04_0188:

Deleting a Visualization Job
============================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Delete a visualization job based on the specified **visualization_id**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import VisualizationJob
      session = Session()
      job = VisualizationJob(modelarts_session=session, visualization_id='8992')
      status = job.delete_visualization_job()

-  Method 2: Delete the visualization job created in :ref:`Creating a Visualization Job <modelarts_04_0181>`.

   ::

      status = job_visualization_instance.delete_visualization_job()

-  Method 3: Delete the visualization job object returned in :ref:`Querying the List of Visualization Job Objects <modelarts_04_0182>`.

   ::

      status = job_visualization_instance_list[0].delete_visualization_job()

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

.. table:: **Table 2** **delete_visualization_job** response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================+
   | error_code            | String                | Error code when the API fails to be called. For details, see `Error Codes <https://docs.otc.t-systems.com/modelarts/api-ref/common_parameters/error_codes.html>`__ in *ModelArts API Reference*. |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_msg             | String                | Error message when the API call fails.                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                  |
   |                       |                       | This parameter is not included when the API call succeeds.                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_success            | Boolean               | Whether the API call succeeds                                                                                                                                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
