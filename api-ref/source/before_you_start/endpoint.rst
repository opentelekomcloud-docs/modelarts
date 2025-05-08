:original_name: modelarts_03_0141.html

.. _modelarts_03_0141:

Endpoint
========

An endpoint is the request address for calling an API. Endpoints vary depending on services and regions. To obtain the regions and endpoints, contact the enterprise administrator.

A service endpoint consists of the service name, region ID, and external domain name in the format of "{service_name}.{region_id}.{external_domain_name}". :ref:`Table 1 <en-us_topic_0000002268848205__en-us_topic_0000001072357044_table24011519165716>` describes these parameters.

.. _en-us_topic_0000002268848205__en-us_topic_0000001072357044_table24011519165716:

.. table:: **Table 1** Endpoint parameters

   +----------------------+-------------------------------------------------+---------------------------------------------+
   | Parameter            | Description                                     | How to Obtain                               |
   +======================+=================================================+=============================================+
   | service_name         | Abbreviation of a case-insensitive service name | **modelarts** for ModelArts by default.     |
   +----------------------+-------------------------------------------------+---------------------------------------------+
   | region_id            | Region ID                                       | Contact the system administrator to obtain. |
   +----------------------+-------------------------------------------------+---------------------------------------------+
   | external_domain_name | External domain name suffix                     | Contact the system administrator to obtain. |
   +----------------------+-------------------------------------------------+---------------------------------------------+

.. important::

   If an endpoint uses a domain name, configure the hosts file in the format of "{float-ip} {service_name}.{region_id}.{external_domain_name}" on the local PC. Contact the system administrator to obtain **float-ip**.
