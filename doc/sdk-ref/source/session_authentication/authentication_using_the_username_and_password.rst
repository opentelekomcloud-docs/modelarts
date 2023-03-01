:original_name: modelarts_04_0154.html

.. _modelarts_04_0154:

Authentication Using the Username and Password
==============================================

This authentication method is available for :ref:`OBS Management <modelarts_04_0217>`, :ref:`Training Management <modelarts_04_0131>`, :ref:`Model Management <modelarts_04_0194>`, and :ref:`Service Management <modelarts_04_0200>`.

Sample Code
-----------

Set **account** to your domain name and **username** to your username.

::

   from modelarts.session import Session
   # Set endpoint
   Session.set_endpoint(iam_endpoint='***',
                        obs_endpoint='***',
                        modelarts_endpoint='***',
                        region_name='***')
   session = Session(account='***', username='***',  password='***', region_name='***', project_id='***')
