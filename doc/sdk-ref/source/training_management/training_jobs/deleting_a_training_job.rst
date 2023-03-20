:original_name: modelarts_04_0166.html

.. _modelarts_04_0166:

Deleting a Training Job
=======================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

Method 1: Delete a training job based on the specified **job_id**.

::

   from modelarts.session import Session
   from modelarts.estimator import Estimator
   session = Session()
   Estimator.delete_job_by_id(modelarts_session=session, job_id="155500")

Method 2: Delete the training job created in :ref:`Creating a Training Job <modelarts_04_0131>`.

::

   status = job_instance.delete_job()

Parameter Description
---------------------

.. table:: **Table 1** **delete_job_by_id** request parameters

   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                                                                                                                                                                              |
   +===================+===========+========+==========================================================================================================================================================================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                                      |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id            | Yes       | String | ID of a training job. You can query **job_id** using the training job object generated in :ref:`Creating a Training Job <modelarts_04_0131>`, for example, **job_instance.job_id**, or from the response obtained in :ref:`Obtaining Training Jobs <modelarts_04_0160>`. |
   +-------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **delete_job_by_id** response parameters

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | error_msg             | String                | Error message when the API call fails.                     |
   |                       |                       |                                                            |
   |                       |                       | This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | error_code            | String                | Error code when the API call fails.                        |
   |                       |                       |                                                            |
   |                       |                       | This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | is_success            | Boolean               | Whether the API call succeeds                              |
   +-----------------------+-----------------------+------------------------------------------------------------+
