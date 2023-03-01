:original_name: modelarts_04_0155.html

.. _modelarts_04_0155:

AK/SK-based Authentication
==========================

This authentication method is available for :ref:`OBS Management <modelarts_04_0217>`, :ref:`Training Management <modelarts_04_0131>`, :ref:`Model Management <modelarts_04_0194>`, and :ref:`Service Management <modelarts_04_0200>`.

Sample Code
-----------

::

   from modelarts.session import Session
   # Set endpoint
   Session.set_endpoint(iam_endpoint='***',
                        obs_endpoint='***',
                        modelarts_endpoint='***',
                        region_name='***')
   session = Session(access_key='***',secret_key='***', project_id='***', region_name='***')

Parameters in this command are described as follows:

-  For details about how to obtain the values of **access_key** and **secret_key**, see `Obtaining an Access Key <https://docs.otc.t-systems.com/modelarts/umn/preparations/configuring_access_authorization_global_configuration/configuring_access_key_authorization.html#obtaining-an-access-key>`__.
-  **project_id** indicates the project ID.
-  **region_name** indicates the region ID. Obtain the region ID from the system administrator.
