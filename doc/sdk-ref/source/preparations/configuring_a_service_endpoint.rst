:original_name: modelarts_04_0300.html

.. _modelarts_04_0300:

Configuring a Service Endpoint
==============================

Using the SDK in non-notebook environments needs to call IAM, OBS, and ModelArts. Therefore, the endpoints of these services are required. Therefore, the endpoints of these services are required. To obtain the endpoints, configure as follows:

.. code-block::

   from modelarts.session import Session
   Session.set_endpoint(iam_endpoint="***", obs_endpoint="***", modelarts_endpoint="***", region_name="***")

.. table:: **Table 1** Parameters

   ================== ==================
   Parameter          Description
   ================== ==================
   iam_endpoint       IAM endpoint
   obs_endpoint       OBS endpoint
   modelarts_endpoint ModelArts endpoint
   region_name        Region name
   ================== ==================
