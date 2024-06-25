:original_name: modelarts_trouble_0035.html

.. _modelarts_trouble_0035:

Error Message "errorMessage:The specified key does not exist" Displayed in Logs
===============================================================================

Symptom
-------

When MoXing is used to access an OBS path, the following error is displayed:

.. code-block::

   ERROR:root:
   stat:404
   errorCode:NoSuchKey
   errorMessage:The specified key does not exist.

Possible Causes
---------------

The possible causes are as follows:

The object is unavailable in the bucket. For details about OBS error codes, see **Python > Troubleshooting > OBS Server-Side Error Codes** in *Object Storage Service SDK Reference*.

Solution
--------

#. Check whether the OBS path and object are in correct format.
#. Use the local PyCharm to remotely access notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use a ModelArts development environment to debug training code. This maximally eliminates errors in code migration.
