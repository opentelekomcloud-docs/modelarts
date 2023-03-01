:original_name: modelarts_23_0061.html

.. _modelarts_23_0061:

Viewing Service Details
=======================

After a model is deployed as a real-time service, you can access the service page to view its details.

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.

#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed.

   You can view the service name and status. For details, see :ref:`Table 1 <modelarts_23_0061__en-us_topic_0165025305_table54131529105213>`.

   .. _modelarts_23_0061__en-us_topic_0165025305_table54131529105213:

   .. table:: **Table 1** Real-time service parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                               |
      +===================================+===========================================================================================================================+
      | Name                              | Name of the real-time service.                                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Current status of the real-time service.                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Source                            | Model source of the real-time service.                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Failed Calls/Total Calls          | Number of service calls, which is counted from the time when the service was created.                                     |
      |                                   |                                                                                                                           |
      |                                   | If the number of models is changed or a service is invoked when a model is not ready, the number of calls is not counted. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Service description, which can be edited after you click the edit button on the right side.                               |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Traffic Limit                     | Maximum number of times a service can be accessed within a second.                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------+

#. You can switch between tabs on the details page of a real-time service to view more details. For details, see :ref:`Table 2 <modelarts_23_0061__en-us_topic_0165025305_table62441712183917>`.

   .. _modelarts_23_0061__en-us_topic_0165025305_table62441712183917:

   .. table:: **Table 2** Service details

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================================+
      | Usage Guides                      | Displays the API address, model information, input parameters, and output parameters. You can click |image1| to copy the API address to call the service.                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prediction                        | Performs a prediction test on the real-time service. For details, see :ref:`Testing a Service <modelarts_23_0062>`.                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Configuration Updates             | Displays **Existing Configuration** and **Historical Updates**.                                                                                                                                 |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  **Existing Configuration**: includes the model name, version, status, traffic ratio, .                                                                                                       |
      |                                   | -  **Historical Updates**: displays historical model information.                                                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Monitoring                        | Displays **Resource Usage** and **Model Calls**.                                                                                                                                                |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  **Resource Usage**: includes the used and available CPU, memory, and GPU resources.                                                                                                          |
      |                                   | -  **Model Calls**: indicates the number of model calls. The statistics collection starts after the model status changes to **Ready**.                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event                             | Displays key operations during service use, such as the service deployment progress, detailed causes of deployment exceptions, and time points when a service is started, stopped, or modified. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Logs                              | Displays the log information about each model in the service. You can view logs generated in the latest 5 minutes, latest 30 minutes, latest 1 hour, and user-defined time segment.             |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  You can select the start time and end time when defining the time segment.                                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001404666210.png
