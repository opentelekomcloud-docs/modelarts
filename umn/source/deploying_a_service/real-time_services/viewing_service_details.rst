:original_name: modelarts_23_0061.html

.. _modelarts_23_0061:

Viewing Service Details
=======================

After an AI application is deployed as a real-time service, you can access the service page to view its details.

#. Log in to the ModelArts management console and choose **Service Deployment** > **Real-Time Services**.

#. On the **Real-Time Services** page, click the name of the target service. The service details page is displayed.

   You can view the service name, status, and other information. For details, see :ref:`Table 1 <modelarts_23_0061__en-us_topic_0165025305_table54131529105213>`.

   .. _modelarts_23_0061__en-us_topic_0165025305_table54131529105213:

   .. table:: **Table 1** Real-time service parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                  |
      +===================================+==============================================================================================================================================+
      | Name                              | Name of the real-time service.                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Status                            | Current status of the real-time service.                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Failed Calls/Total Calls          | Number of service calls, which is counted from the time when the service was created.                                                        |
      |                                   |                                                                                                                                              |
      |                                   | If the number of AI applications is changed or a service is invoked when an AI application is not ready, the number of calls is not counted. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Service ID                        | Real-time service ID.                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Source                            | AI application source of the real-time service.                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Service description, which can be edited after you click the edit button on the right side.                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------+

#. You can switch between tabs on the details page of a real-time service to view more details. For details, see :ref:`Table 2 <modelarts_23_0061__en-us_topic_0165025305_table62441712183917>`.

   .. _modelarts_23_0061__en-us_topic_0165025305_table62441712183917:

   .. table:: **Table 2** Service details

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================================+
      | Usage Guides                      | Displays the API address, AI application information, input parameters, and output parameters. You can click |image1| to copy the API address to call the service.                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prediction                        | Performs a prediction test on the real-time service. For details, see :ref:`Testing a Service <modelarts_23_0062>`.                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Configuration Updates             | Displays **Existing Configuration** and **Historical Updates**.                                                                                                                                 |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  **Existing Configuration**: includes the AI application name, version, status, and traffic ratio.                                                                                            |
      |                                   | -  **Historical Updates**: displays historical AI application information.                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Monitoring                        | Displays **Resource Usage** and **AI Application Calls**.                                                                                                                                       |
      |                                   |                                                                                                                                                                                                 |
      |                                   | -  **Resource Usage**: includes the used and available CPU, memory, and GPU resources.                                                                                                          |
      |                                   | -  **AI Application Calls**: indicates the number of AI application calls. The statistics collection starts after the AI application status changes to **Ready**.                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Event                             | Displays key operations during service use, such as the service deployment progress, detailed causes of deployment exceptions, and time points when a service is started, stopped, or modified. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Logs                              | Displays the log information about each AI application in the service. You can view logs generated in the latest 5 minutes, latest 30 minutes, latest 1 hour, and user-defined time segment.    |
      |                                   |                                                                                                                                                                                                 |
      |                                   | You can select the start time and end time when defining the time segment.                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001846057553.png
