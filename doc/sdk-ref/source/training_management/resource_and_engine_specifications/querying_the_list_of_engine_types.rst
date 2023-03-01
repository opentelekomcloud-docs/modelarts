:original_name: modelarts_04_0192.html

.. _modelarts_04_0192:

Querying the List of Engine Types
=================================

Sample Code
-----------

In the ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

::

   from modelarts.session import Session
   from modelarts.estimator import Estimator
   session = Session()
   engine_list = Estimator.get_framework_list(modelarts_session=session)

Parameter Description
---------------------

.. table:: **Table 1** **get_framework_list** parameters

   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                         |
   +===================+===========+========+=====================================================================================================================+
   | modelarts_session | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`. |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Successful response parameters of **get_framework_list**

   +------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type | Description                                                                                                                                               |
   +======+===========================================================================================================================================================+
   | List | List of engine flavor attributes. For details, see :ref:`Table 3 <modelarts_04_0192__en-us_topic_0180094061_en-us_topic_0160574647_table14718195812596>`. |
   +------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _modelarts_04_0192__en-us_topic_0180094061_en-us_topic_0160574647_table14718195812596:

.. table:: **Table 3** **framework_list** parameters

   ================= ====== ==============
   Parameter         Type   Description
   ================= ====== ==============
   framework_type    String Engine type
   framework_version String Engine version
   ================= ====== ==============

.. table:: **Table 4** Failed response parameters

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
