:original_name: modelarts_trouble_0111.html

.. _modelarts_trouble_0111:

Suspension Before Training
==========================

If a job is trained on multiple nodes and suspension occurs before the job starts, add **os.environ["NCCL_DEBUG"] = "INFO"** to the code to view the NCCL debugging information.

Symptom 1
---------

The job is suspended before the NCCL debugging information is displayed in logs.

Solution 1
----------

Check the code for parameters such as **master_ip** and **rank**. Ensure that these parameters are specified.

Symptom 2
---------

The GDR information is displayed only on certain nodes of a multi-node training job.

|image1|

The possible cause of the suspension is GDR.

|image2|

Solution 2
----------

Set **os.environ["NCCL_NET_GDR_LEVEL"] = '0'** at the beginning of the program or ask the O&M personnel to add the GDR information to the affected nodes.

Symptom 3
---------

Communication information such as "Got completion with error 12, opcode 1, len 32478, vendor err 129" is displayed. The current network is unstable.

Solution 3
----------

Add the following environment variables:

-  **NCCL_IB_GID_INDEX=3**: enables RoCEv2. RoCEv1 is enabled by default. However, RoCEv1 does not support congestion control on switches, which may lead to packet loss. In addition, later-version switches do not support RoCEv1, leading to a RoCEv1 failure.
-  **NCCL_IB_TC=128**: enables data packets to be transmitted through the queue 4 of switches, which is RoCE-compliant.
-  **NCCL_IB_TIMEOUT=22**: enables a longer timeout interval. Generally, there is a network interruption lasting about 5s if the network is unstable and then the timeout message is returned. Change the timeout interval to 22s, indicating that the timeout message will be returned in about 20s (4.096 µs x 2 ^ timeout).

For more details, see https://docs.nvidia.com/deeplearning/nccl/user-guide/docs/env.html#nccl-ib-timeout.

.. |image1| image:: /_static/images/en-us_image_0000002268820341.jpg
.. |image2| image:: /_static/images/en-us_image_0000002268740421.jpg
