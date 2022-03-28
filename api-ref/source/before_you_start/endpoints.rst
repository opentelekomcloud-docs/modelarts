Endpoints
=========

Endpoints are **request address** for calling APIs. Endpoints vary depending on services and regions. To obtain the regions and endpoints, contact the enterprise administrator.

A service endpoint consists of the service name, region ID, and external domain name in the format of "{service_name}.{region_id}.{external_domain_name}". For details about how to obtain each parameter, see `Table 1 <#modelarts030141enustopic0000001072357044table8700253831>`__.



.. _modelarts030141enustopic0000001072357044table8700253831:

.. table:: **Table 1** Obtaining an endpoint

   +----------------------+-------------------------------------------------+------------------------------------------+
   | Parameter            | Description                                     | How to Obtain                            |
   +======================+=================================================+==========================================+
   | service_name         | Abbreviation of a case-insensitive service name | **modelarts** for ModelArts by default.  |
   +----------------------+-------------------------------------------------+------------------------------------------+
   | region_id            | Region ID                                       | Obtain the value from the administrator. |
   +----------------------+-------------------------------------------------+------------------------------------------+
   | external_domain_name | External domain name suffix                     | Obtain the value from the administrator. |
   +----------------------+-------------------------------------------------+------------------------------------------+

.. important::

   If an endpoint uses a domain name, configure the hosts file in the format of "{float-ip} {service_name}.{region_id}.{external_domain_name}" on the local PC. Obtain **float-ip** from the administrator.


