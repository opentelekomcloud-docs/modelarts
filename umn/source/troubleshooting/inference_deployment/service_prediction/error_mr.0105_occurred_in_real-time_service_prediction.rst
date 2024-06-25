:original_name: modelarts_13_0192.html

.. _modelarts_13_0192:

Error MR.0105 Occurred in Real-Time Service Prediction
======================================================

Symptom
-------

During the prediction in a running real-time service, error { "erno": "MR.0105", "msg": "Recognition failed","words_result": {}} occurred.

Possible Causes
---------------

Locate the fault by analyzing the error log on the **Logs** tab of the real-time service details page.

According to the error log shown in the preceding figure, the prediction failure is caused by the model inference code.

Solution
--------

According to the error log, mandatory parameters are missing in the append() method. To rectify the fault, modify the code in the model inference code file **customize_service.py** to transfer proper parameters to the append() method.
