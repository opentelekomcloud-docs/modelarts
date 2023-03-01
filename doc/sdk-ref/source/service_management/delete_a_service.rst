:original_name: modelarts_04_0211.html

.. _modelarts_04_0211:

Delete a Service
================

You can delete a service in either of the following ways:

-  Delete the service created in :ref:`Deploying a Real-Time Service <modelarts_04_0201>`.
-  Delete the service object returned in :ref:`Querying the List of Service Objects <modelarts_04_0206>`.

Sample Code
-----------

In a ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Delete the service created in :ref:`Deploying a Real-Time Service <modelarts_04_0201>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_instance = Predictor(session, service_id="input your service_id")
      predictor_instance.delete_service()

-  Method 2: Delete the service object returned in :ref:`Querying the List of Service Objects <modelarts_04_0206>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Predictor
      session = Session()
      predictor_object_list = Predictor.get_service_object_list(session)
      predictor_instance = predictor_object_list[0]
      predictor_instance.delete_service()
