:original_name: modelarts_04_0004.html

.. _modelarts_04_0004:

Downloading and Installing the SDK
==================================

Download ModelArts SDK
----------------------

`Download the ModelArts SDK software package <https://obs-sdk.obs.eu-de.otc.t-systems.com/modelarts-latest-py2.py3-none-any.whl>`__ of the latest version.

Installing the SDK
------------------

After the SDK is downloaded, you can use pip to install it. For details about how to install pip, see the `pip official website <https://pip.pypa.io/en/stable/installation/>`__. To install the ModelArts SDK, run the following command:

**pip install modelarts-latest-py2.py3-none-any.whl**

The required dependency packages are installed by default during SDK installation. The details are as follows:

.. code-block::

   certifi >= 14.05.14
   six >= 1.10
   python_dateutil >= 2.5.3
   setuptools >= 21.0.0
   urllib3 >= 1.15.1
   requests >= 2.19.1
   esdk-obs-python == 3.0.5
   Flask==1.0.2
   Flask-Cors==3.0.4
   gunicorn==19.8.1
   mxnet-model-server==0.3
   psutil==5.4.6
   prometheus_client==0.3.1

If an error message is displayed during the installation, indicating that a required dependency package is missing, run the following command to install the dependency package as prompted. In the command, *xxxx* indicates the name of the dependency package.

**pip install xxxx**
