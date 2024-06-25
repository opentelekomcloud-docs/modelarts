:original_name: modelarts_23_0302_0.html

.. _modelarts_23_0302_0:

Creating a Hyperparameter Search Job
====================================

Background
----------

Hyperparameters that you want to optimize need to be defined when you configure **Hyperparameters**. You can specify the name, type, default value, and constraints. For details, see :ref:`Defining Hyperparameters <en-us_topic_0000001910016246__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1883311313516>`.

If the AI engine is **PyTorch-1.4.0-python3.6-v2** or **TF-1.13.1-python3.6-v2** and the hyperparameter to be optimized is of the float type, you can use hyperparameter search on ModelArts.

You can perform the hyperparameter search without any code modification. The procedure is as follows:

#. :ref:`Preparations <en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section19539763520>`
#. :ref:`Creating an Algorithm <en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section54440253422>`
#. :ref:`Creating a Training Job (New) <en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section3995430104214>`
#. :ref:`Viewing Details About a Hyperparameter Search Job <en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section1194724314164>`

.. _en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section19539763520:

Preparations
------------

-  Data has been prepared. Specifically, you have created an available dataset in ModelArts, or you have uploaded the dataset used for training to the OBS directory.
-  You need to prepare the training script and upload it to the OBS directory. For details about how to develop a training script, see :ref:`Developing a Custom Script <develop-modelarts-0008>`.
-  In the training code, you need to print the search indicator parameters.
-  At least one empty folder has been created in OBS for storing the training output.
-  The OBS directory you use and ModelArts are in the same region.

.. _en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section54440253422:

Creating an Algorithm
---------------------

Log in to the ModelArts management console and create an algorithm by referring to :ref:`Creating an Algorithm <develop-modelarts-0009>`. When configuring parameters of the algorithm, pay attention to the configuration of **Hyperparameters** and **Supported Policies**.


.. figure:: /_static/images/en-us_image_0000001805726206.png
   :alt: **Figure 1** Parameters of hyperparameter search

   **Figure 1** Parameters of hyperparameter search

Hyperparameters that you want to optimize need to be defined when you configure **Hyperparameters**. You can specify the name, type, default value, and constraints. For details, see :ref:`Defining Hyperparameters <en-us_topic_0000001910016246__en-us_topic_0000001133351332_en-us_topic_0000001071986951_section1883311313516>`.

Select **autoSearch(S)** to enable the auto search function for the algorithm. During an auto search, ModelArts uses a regular expression to obtain the search indicator parameters and performs hyperparameter optimization based on the optimization direction. You need to print search parameters in the code and configure the following parameters:

-  Search Indicator

   The search indicator is the value of the objective function, which can be loss, accuracy, and so on. By optimizing and converging this value based on the optimization direction, the optimal hyperparameter can be found to improve the model precision and convergence speed.

   .. table:: **Table 1** Search indicator parameters

      +------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter              | Description                                                                                                                        |
      +========================+====================================================================================================================================+
      | Name                   | search indicator name. This parameter must be identical to the search indicator parameter in the code.                             |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Optimization Direction | This parameter can be **max** or **min**.                                                                                          |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Counter regularization | A regular expression needs to be entered. You can click **Generate Intelligently** to generate a regular expression automatically. |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------+

-  Setting Automatic Search Parameters

   Select hyperparameters that can be used for search optimization from what you configured for **Hyperparameters**. Only hyperparameters of the float type are supported. After **autoSearch(S)** is selected, set the value range.

-  Search Algorithm Configuration

   ModelArts has three built-in algorithms for hyperparameter search. You can select one or more algorithms as needed. The algorithms and their parameter description are as follows:

   -  bayes_opt_search: :ref:`Bayesian Optimization (SMAC) <en-us_topic_0000001916662106>`
   -  tpe_search: :ref:`TPE Algorithm <en-us_topic_0000001947261241>`
   -  anneal_search: :ref:`Simulated Annealing Algorithm <en-us_topic_0000001916502166>`

After you submit the request for creating the algorithm, wait until the algorithm is available on the algorithm management page. When the newly created algorithm is available, you can perform other operations.

.. _en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section3995430104214:

Creating a Training Job (New)
-----------------------------

Log in to the ModelArts management console and create a training job by referring to :ref:`Creating a Training Job <develop-modelarts-0011>`. Pay attention to operations described in this section before you enable the hyperparameter search.

If you select an algorithm that supports hyperparameter search, you need to click the button for range setting to enable hyperparameter search.

After the hyperparameter search is enabled, you can configure the search indicator, search algorithm, and parameters of the selected algorithm. These parameters need to have the same values as the hyperparameters of the algorithm you created.

After a hyperparameter search job is created, it will take a period of time to run it.

.. _en-us_topic_0000001916662110__en-us_topic_0000001846056413_en-us_topic_0000001159996229_section1194724314164:

Viewing Details About a Hyperparameter Search Job
-------------------------------------------------

After a training job is complete, you can view the job details to determine whether the training job is satisfactory.

You can go to the ModelArts management console to view the details. For details, see :ref:`Viewing Training Job Details <develop-modelarts-0013>`. If the training job is an auto hyperparameter search job, you can view the results after it is completed.
