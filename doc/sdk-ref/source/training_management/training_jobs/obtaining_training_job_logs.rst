:original_name: modelarts_04_0164.html

.. _modelarts_04_0164:

Obtaining Training Job Logs
===========================

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Use the specified **job_id** and **version_id**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(modelarts_session=session, job_id="182626", version_id="278813")
      job_log = estimator.get_job_log(log_file='job-job-0713-191758.0')

-  Method 2: Use the training job created in :ref:`Creating a Training Job <modelarts_04_0131>`.

   ::

      job_log = job_instance.get_job_log(log_file='job-job-0713-191758.0')

-  Method 3: Use the training job version object returned in :ref:`Querying the List of Training Job Versions <modelarts_04_0169>`.

   ::

      job_log = job_version_instance_list[0].get_job_log(log_file='job-job-0713-191758.0')

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                                                                                                                                                                              |
   +===================+===========+========+==========================================================================================================================================================================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                                      |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id            | Yes       | String | ID of a training job. Obtain **job_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.job_id**, or from the response in :ref:`Obtaining Training Jobs <modelarts_04_0160>`.                 |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version_id        | Yes       | String | Version ID of a training job. Obtain **version_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.version_id**, or from the response in :ref:`Obtaining Training Jobs <modelarts_04_0160>`. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **get_job_log** request parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                                                        |
   +============+===========+========+====================================================================================================================================================================+
   | log_file   | Yes       | String | Name of a training job log file                                                                                                                                    |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_byte | No        | Long   | Start position for obtaining the log. The default value is **0**. The value range is [-1, +∞]. If the value is **-1**, the log with the latest offset is obtained. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset     | No        | Long   | Length of the obtained log. The default value is **2048**. The value range is [-2048, 2048].                                                                       |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **get_job_log** response parameters

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
   | content               | String                | Content of the requested log                                                                                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lines                 | Integer               | Number of lines in the log                                                                                                                                                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_line            | String                | Start position of the obtained log                                                                                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_line              | String                | End position of the obtained log                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
