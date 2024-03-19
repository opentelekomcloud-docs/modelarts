:original_name: modelarts_01_0021.html

.. _modelarts_01_0021:

Billing
=======

ModelArts is a one-stop AI development platform geared toward developers and data scientists of all skill levels. It enables you to rapidly build, train, and deploy models anywhere (from the cloud to the edge), and manage full-lifecycle AI workflows. ModelArts accelerates AI development and fosters AI innovation with key capabilities, including data preprocessing and auto labeling, distributed training, automated model building, and one-click workflow executing.

ModelArts is flexibly billed based on service duration.

Billing Items
-------------

The fees vary based on selected ModelArts resources. For details, see :ref:`Table 1 <modelarts_01_0021__table15783184319374>`.

.. _modelarts_01_0021__table15783184319374:

.. table:: **Table 1** Billing items

   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Billing Item                | Description                                                                                                                                                                                                                                                                                                                                                                                                             |
   +=============================+=========================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Full-process AI development | Dedicated for developers with AI development experience. ModelArts offers machine learning and deep learning algorithm development and deployment, including data processing, model development, training, and management, and service deployment. The billing items include model development environments (Notebook), model training (training and virtualization jobs), and service deployment (real-time services). |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ExeML                       | Dedicated for developers with few AI development experience. ModelArts enables code-free custom model development by automatically designing, tuning, and training models based on labeled data, and deploying the models as services. Only the resources used for training and deploying ExeML jobs are billed. The billing items include training jobs, GPU deployment, and CPU deployment in ExeML.                  |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Billing Modes
-------------

**Pay-per-use**: allows you to flexibly enable or disable ModelArts.

Configuration Modification-related Billing
------------------------------------------

You can manually adjust the capacity of a pay-per-use dedicated resource pool. The billing is based on the number of nodes after adjustment.

If the configuration modification methods provided by ModelArts do not meet your requirements, re-create a job and migrate data to it for configuration modification.
