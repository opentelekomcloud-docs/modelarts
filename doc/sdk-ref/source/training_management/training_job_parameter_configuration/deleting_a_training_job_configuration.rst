:original_name: modelarts_04_0179.html

.. _modelarts_04_0179:

Deleting a Training Job Configuration
=====================================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Delete a training job parameter configuration based on the specified **config_name**.

   ::

      from modelarts.session import Session
      from modelarts.estimator import Estimator
      session = Session()
      estimator = Estimator(modelarts_session=session, config_name="my_job_config")
      status = estimator.delete_job_configs()

-  Method 2: Delete the training job parameter configuration created in :ref:`Creating a Training Job Configuration <modelarts_04_0174>`.

   ::

      status = job_config_instance.delete_job_configs()

-  Method 3: Delete the training job parameter configuration object returned in :ref:`Querying the List of Training Job Parameter Configuration Objects <modelarts_04_0175>`.

   ::

      status = job_config_instance_list[0].delete_job_configs()

Parameter Description
---------------------

.. table:: **Table 1** Estimator request parameters

   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                         |
   +===================+===========+========+=====================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`. |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | config_name       | Yes       | String | Name of a training job parameter configuration                                                                      |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** **delete_job_configs** response parameters

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
