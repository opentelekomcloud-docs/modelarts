:original_name: modelarts_04_0123.html

.. _modelarts_04_0123:

Overview of Session Authentication
==================================

The session module authenticates in-cloud resources and initializes ModelArts SDK Client and OBS Client. After a session is set up, you can directly call the ModelArts SDK APIs.

-  ModelArts notebook can be directly used without configuring session authentication parameters. The sample code is as follows:

   ::

      from modelarts.session import Session
      session = Session()

-  When using the ModelArts SDK in other development environments, select one of the following authentication methods for session authentication:

   -  :ref:`Authentication Using the Username and Password <modelarts_04_0154>`: Available for :ref:`OBS Management <modelarts_04_0217>`, :ref:`Training Management <modelarts_04_0131>`, :ref:`Model Management <modelarts_04_0194>`, and :ref:`Service Management <modelarts_04_0200>`.
   -  :ref:`AK/SK-based Authentication <modelarts_04_0155>`: Available for :ref:`OBS Management <modelarts_04_0217>`, :ref:`Training Management <modelarts_04_0131>`, :ref:`Model Management <modelarts_04_0194>`, and :ref:`Service Management <modelarts_04_0200>`.
