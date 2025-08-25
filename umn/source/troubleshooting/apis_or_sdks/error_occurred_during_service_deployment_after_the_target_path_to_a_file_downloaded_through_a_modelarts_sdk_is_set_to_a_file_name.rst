:original_name: modelarts_13_0199.html

.. _modelarts_13_0199:

Error Occurred During Service Deployment After the Target Path to a File Downloaded Through a ModelArts SDK Is Set to a File Name
=================================================================================================================================

Symptom
-------

A ModelArts SDK was used to download a file from OBS, and the target path was set to the file name. No error was reported in the local IDE, but an error occurred when the target model was deployed as a real-time service.

Sample code:

.. code-block::

   session.obs.download_file (obs_path, local_path)

The error message is as follows:

.. code-block::

   2022-07-06 16:22:36 CST [ThreadPoolEx] - /home/work/predict/model/customize_service.py[line:184] - WARNING: 4 try: IsADirectoryError(21, 'Is a directory'). update products failed!

Possible Causes
---------------

The target path (**local_path**) was incorrectly set in code.

Solution
--------

Set **local_path** to a folder and ensure the folder name extension ends with a slash (/).
