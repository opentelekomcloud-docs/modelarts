:original_name: modelarts_trouble_0040.html

.. _modelarts_trouble_0040:

Error Message "Pod The node was low on resource:[DiskPressure]" Displayed in the Kubernetes Job Body
====================================================================================================

Symptom
-------

Executing a training job failed, and there is no error message in user logs. The error information is displayed in the Kubernetes job body.


.. figure:: /_static/images/en-us_image_0000001846057173.png
   :alt: **Figure 1** Kubernetes job body

   **Figure 1** Kubernetes job body

Possible Causes
---------------

The possible causes are as follows:

The disk space is insufficient.

Solution
--------

#. Rectify the fault by referring to solutions in :ref:`Error Message "write line error" Displayed in Logs <modelarts_trouble_0031__en-us_topic_0000001192868375_en-us_topic_0000001135764558_en-us_topic_0192056517_section520813413313>` and :ref:`Error Message "No space left on device" Displayed in Logs <modelarts_trouble_0041__en-us_topic_0000001192988243_en-us_topic_0000001136263284_en-us_topic_0192056517_section520813413313>`.
#. Use the local PyCharm to remotely connect to the notebook for debugging.
