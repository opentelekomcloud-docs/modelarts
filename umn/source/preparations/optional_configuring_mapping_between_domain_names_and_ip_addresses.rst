:original_name: modelarts_08_0008.html

.. _modelarts_08_0008:

(Optional) Configuring Mapping Between Domain Names and IP Addresses
====================================================================

If the domain name of a region can be resolved through the public network, skip in this section. If the domain name of a region cannot be resolved through the public network, perform the operations described in this section to configure the mapping between domain names and IP addresses in the hosts file on the local computer.

Procedure
---------

Configure the domain names and IP addresses of IAM, OBS, and ModelArts in **C:\\Windows\\System32\\drivers\\etc\\hosts** on a local computer. Contact technical support for the domain names and IP addresses. The following shows an example configuration:

.. code-block::

   xxx.xxx.xxx.xxx      modelarts.xxx.xxx.com
   xxx.xxx.xxx.xxx      iam.xxx.xxx.com
   xxx.xxx.xxx.xxx      obs.xxxx.xxx.com
   xxx.xxx.xxx.xxx      swr.xxx.xxx.com

.. note::

   The domain name of a region is an endpoint, which can be obtained from `Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.
