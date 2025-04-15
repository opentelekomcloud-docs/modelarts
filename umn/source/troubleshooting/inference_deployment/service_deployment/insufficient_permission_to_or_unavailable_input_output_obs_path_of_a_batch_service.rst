:original_name: modelarts_13_0251.html

.. _modelarts_13_0251:

Insufficient Permission to or Unavailable Input/Output OBS Path of a Batch Service
==================================================================================

Symptom
-------

#. An input/output path is unavailable, and the following error message is displayed:

   .. code-block::

      "error_code": "ModelArts.3551",
      "error_msg": "OBS path xxxx does not exist."

#. When the access to an input/output path is denied, the following error message is displayed:

   .. code-block::

      "error_code": "ModelArts.3567",
      "error_msg": "OBS error occurs because Access Denied."

Possible Causes
---------------

ModelArts.3551: The OBS path for data input or output does not exist.

ModelArts.3567: The OBS path for data input or output is available, but the current account does not have the permission to access the path.

Solution
--------

ModelArts.3551: Check whether the data input path is available in OBS. If not, create an OBS path as required. If the path is available but the error persists, submit a service ticket to apply for technical support.

ModelArts.3567: You can access only the OBS path under your own account. To read the OBS data of other users through ModelArts, configure an agency. Otherwise, the access is denied.

Log in to the ModelArts management console. In the navigation pane, choose **Settings**. Click **View Permissions** to check whether the OBS agency permission is configured.


.. figure:: /_static/images/en-us_image_0000002233899864.png
   :alt: **Figure 1** Viewing permissions

   **Figure 1** Viewing permissions

If an agency already exists but the error persists, submit a service ticket for technical support.
