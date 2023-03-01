:original_name: modelarts_04_0191.html

.. _modelarts_04_0191:

Querying the List of Resource Flavors
=====================================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

::

   from modelarts.session import Session
   from modelarts.estimator import Estimator
   session = Session()
   algo_info = Estimator.get_train_instance_types(modelarts_session=session)

Parameter Description
---------------------

.. table:: **Table 1** Request parameters

   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                         |
   +===================+===========+========+=====================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`. |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Successful response parameters

   ==== ==================================
   Type Description
   ==== ==================================
   List List of resource flavor attributes
   ==== ==================================

.. table:: **Table 3** Failed response parameters

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | error_code            | String                | Error code when the API call fails.                        |
   |                       |                       |                                                            |
   |                       |                       | This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | error_msg             | String                | Error message when the API call fails.                     |
   |                       |                       |                                                            |
   |                       |                       | This parameter is not included when the API call succeeds. |
   +-----------------------+-----------------------+------------------------------------------------------------+
