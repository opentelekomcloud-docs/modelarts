:original_name: resmgmt-modelarts_0008.html

.. _resmgmt-modelarts_0008:

Changing Job Types Supported by a Resource Pool
===============================================

Description
-----------

ModelArts supports many types of jobs. Some of them can run in dedicated resource pools, including training jobs, inference services, and notebook development environments.

You can change job types supported by a dedicated resource pool. Available options for **Job Type** are **Training Job**, **Inference Service**, and **DevEnviron**.

Only selected types of jobs can be delivered to the corresponding dedicated resource pool.

.. caution::

   To support different job types, different operations are performed in the backend, such as installing plug-ins and setting the network environment. Some operations use resources in the resource pool. As a result, available resources for you decrease. Therefore, select only the job types you need to avoid resource waste.

Constraints
-----------

The target dedicated resource pool must be running.

Procedure
---------

#. Log in to the ModelArts management console. In the navigation pane, choose **Dedicated Resource Pools** > **Elastic Cluster**.
#. In the **Operation** column of a resource pool, choose **More** > **Set Job Type**.
#. In the **Set Job Type** dialog box, select job types.
#. Click **OK**.
