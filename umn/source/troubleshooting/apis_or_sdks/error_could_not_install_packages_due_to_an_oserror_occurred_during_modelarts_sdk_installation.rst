:original_name: modelarts_13_0198.html

.. _modelarts_13_0198:

"ERROR: Could not install packages due to an OSError" Occurred During ModelArts SDK Installation
================================================================================================

Symptom
-------

When ModelArts SDKs are installed, the following error message is displayed: "ERROR: Could not install packages due to an OSError: [WinError 2] The system cannot find the file specified: 'c:\\python39\\Scripts\\ephemeral-port-reserve.exe' -> 'c:\\python39\\Scripts\\ephemeral-port-reserve.exe.deleteme".

Possible Causes
---------------

The role of the login user is incorrect.

Solution
--------

Log in to the system as the administrator, press **Windows+R**, enter **cmd**, and run the following command:

.. code-block::

   python -m pip install --upgrade pip
