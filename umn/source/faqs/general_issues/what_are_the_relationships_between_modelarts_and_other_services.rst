:original_name: modelarts_05_0003.html

.. _modelarts_05_0003:

What Are the Relationships Between ModelArts and Other Services?
================================================================

OBS
---

ModelArts uses Object Storage Service (OBS) to securely and reliably store data and models at low costs. For more details, see *Object Storage Service Console Operation Guide*.

CCE
---

ModelArts uses Cloud Container Engine (CCE) to deploy models as real-time services. CCE enables high concurrency and provides elastic scaling. For more information about CCE, see Cloud Container Engine User Guide.

SWR
---

To use an AI framework that is not supported by ModelArts, use Software Repository for Container (SWR) to customize an image and import the image to ModelArts for training or inference. For details about SWR, see .

Cloud Eye
---------

ModelArts uses Cloud Eye to monitor online services and model loads in real time and send alarms and notifications automatically. For details about Cloud Eye, see *Cloud Eye User Guide*.

CTS
---

ModelArts uses Cloud Trace Service (CTS) to record operations for later query, audit, and backtrack operations. For details about CTS, see *Cloud Trace Service User Guide*.
