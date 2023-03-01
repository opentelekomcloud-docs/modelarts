:original_name: modelarts_04_0171.html

.. _modelarts_04_0171:

Stopping a Training Job Version
===============================

You can stop a training job version that is being created only when the job is running.

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Stop a training job version based on the specified **job_id** and **version_id**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(session, job_id="182626", version_id="278813")
      status = estimator.stop_job_version()

-  Method 2: Stop the training job version created in :ref:`Creating a Training Job Version <modelarts_04_0168>`.

   ::

      status = job_version_instance.stop_job_version()

-  Method 3: Stop the training job version object returned in :ref:`Querying the List of Training Job Versions <modelarts_04_0169>`.

   ::

      status = job_version_instance_list[0].stop_job_version()

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
   | version_id        | Yes       | String | Version ID of a training job. You can query **version_id** from the response obtained in :ref:`Querying the List of Training Job Versions <modelarts_04_0169>`.                                                                                                                     |
   +-------------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **stop_job_version** response parameters

   +-----------------------+-----------------------+----------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                    |
   +=======================+=======================+================================================================+
   | error_msg             | String                | Error message when the API call fails.                         |
   |                       |                       |                                                                |
   |                       |                       | This parameter is not included when the API call succeeds.     |
   +-----------------------+-----------------------+----------------------------------------------------------------+
   | error_code            | String                | Error code when the API fails to be called. For details, see . |
   |                       |                       |                                                                |
   |                       |                       | This parameter is not included when the API call succeeds.     |
   +-----------------------+-----------------------+----------------------------------------------------------------+
   | is_success            | Boolean               | Whether the API call succeeds                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------+
