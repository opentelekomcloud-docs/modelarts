:original_name: modelarts_04_0194.html

.. _modelarts_04_0194:

Importing a Model
=================

The model import function covers the following aspects:

-  Initialize the existing model and create a model object based on the model ID.
-  Create a model. For details about the attributes of the created model, see :ref:`Querying the Details About a Model <modelarts_04_0197>`.

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

::

   from modelarts.session import Session
   from modelarts.model import Model
   from modelarts.config.model_config import ServiceConfig,Params,Dependencies,Packages
   session = Session()

-  Method 1: Initialize an existing model.

   ::

      model_instance = Model(session, model_id="input your model id")

-  Method 2: Create a model.

   ::

      model_instance = Model(
                           session,
                           model_name="input model name",              # Model name
                           model_version="1.0.0",                      # Model version
                           source_location=model_location,             # OBS path to a model file, for example, obs://your_obs_bucket/mode_file_path
                           model_type="MXNet",                         # Model type
                           model_algorithm="image_classification",     # Model algorithm
                           execution_code="OBS_PATH",
                           input_params=input_params,                  # For details, see the input_params format description.
                           output_params=output_params,                # For details, see the output_params format description.
                           dependencies=dependencies,                  # For details, see the dependencies format description.
                           apis=apis)

   -  Definition formats of **input_params** and **output_params** parameter groups used in method 2

      The SDK provides the definition of **input_params** and **output_params** parameter groups. The types of **input_params** and **output_params** are list, and those of the tuple objects in the list are Params.

      The following uses **input_params** as an example:

      ::

         input_params = []                                                # The type of input_params is list. Multiple objects of the Params type can be stored.
         input_params1 = Params(
                                 url='url',                               # URL
                                 param_name='param_name',                 # Parameter name
                                 param_type='param_type',                 # Parameter type
                                 min='min',
                                 max='max',
                                 param_desc='param_desc')
         input_params.append(input_params1)

   -  Definition formats of the **dependencies** parameter group used in method 2

      The SDK provides the definition of the **dependencies** parameter group. The type of **dependencies** is list, and those of the tuple objects in the list are Dependencies.

      The code is as follows:

      ::

         dependencies = []
         dependency1 = Dependencies(
                                     installer="pip",                     # Installation mode. pip is supported.
                                     packages=packages)                   # Collection of dependency packages. For details about the definition format, see the definition of packages.
         dependencies.append(dependency1)

   -  Definition formats of the **package** parameter group used in method 2

      The SDK provides the definition of the **packages** parameter group. The type of **packages** is list, and those of the tuple objects in the list are Packages.

      The code is as follows:

      ::

         packages  = []
         package1 =  Packages(
                               package_name="package_name",               # Package name
                               package_version="version",                 # Package version
                               restraint="restraint")
         packages.append(package1)

      .. note::

         The following is an example of creating a **dependencies** parameter group:

         .. code-block::

            dependencies = []
            packages = [{
                        "package_name": "numpy",
                        "package_version": "1.15.0",
                        "restraint": "EXACT"},
                    {
                        "package_name": "h5py",
                        "package_version": "2.8.0",
                        "restraint": "EXACT"}
                      ]
            dependency = Dependencies(installer="pip", packages=packages)
            dependencies.append(dependency)

Parameter Description
---------------------

.. table:: **Table 1** Parameters for initializing a model

   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                         |
   +===========+===========+========+=====================================================================================================================+
   | session   | Yes       | Object | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | model_id  | Yes       | String | Model ID                                                                                                            |
   +-----------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Parameters for creating a model

   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory       | Type                 | Description                                                                                                                                                                                                                                                                                                                                                       |
   +======================+=================+======================+===================================================================================================================================================================================================================================================================================================================================================================+
   | session              | Yes             | Object               | Session object. For details about the initialization method, see :ref:`Session Authentication <modelarts_04_0123>`.                                                                                                                                                                                                                                               |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_name           | No              | String               | Name of a model, which contains 1 to 64 characters that consist of only letters, digits, underscores (_), and hyphens (-). It must start with a letter. If this parameter is not specified, the system automatically generates a model name.                                                                                                                      |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_version        | Yes             | String               | Model version in the format of *Digit.Digit.Digit*. The value range of the digits is [0, 99]. The version number cannot start with 0, for example, **01.01.01**.                                                                                                                                                                                                  |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | publish              | No              | Bool                 | Whether to publish a model. The options are as follows:                                                                                                                                                                                                                                                                                                           |
   |                      |                 |                      |                                                                                                                                                                                                                                                                                                                                                                   |
   |                      |                 |                      | -  **True**: Publish the model. (Default value)                                                                                                                                                                                                                                                                                                                   |
   |                      |                 |                      | -  **False**: Do not publish the model.                                                                                                                                                                                                                                                                                                                           |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_location_type | No              | String               | Model location type. The options are as follows:                                                                                                                                                                                                                                                                                                                  |
   |                      |                 |                      |                                                                                                                                                                                                                                                                                                                                                                   |
   |                      |                 |                      | -  **OBS_SOURCE**: OBS path. (Default value)                                                                                                                                                                                                                                                                                                                      |
   |                      |                 |                      | -  **LOCAL_SOURCE**: local path.                                                                                                                                                                                                                                                                                                                                  |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_location      | Yes             | String               | Path (parent directory) of the model file                                                                                                                                                                                                                                                                                                                         |
   |                      |                 |                      |                                                                                                                                                                                                                                                                                                                                                                   |
   |                      |                 |                      | -  If **source_location_type** is set to **OBS_SOURCE**, the model file path is an OBS path in the format of **/obs_bucketname/.../model_file_parent_dir/**.                                                                                                                                                                                                      |
   |                      |                 |                      | -  If **source_location_type** is set to **LOCAL_SOURCE**, the model file path is a local path in the format of **/local_path/.../model_file_parent_dir/**.                                                                                                                                                                                                       |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | environment          | No              | Environment instance | Environment required for normal model running, such as the Python or TensorFlow version                                                                                                                                                                                                                                                                           |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_job_id        | No              | String               | ID of the source training job. If the model is generated from a training job, specify this parameter for source tracing. If the model is imported from a third-party meta model, leave this parameter blank. By default, this parameter is left blank.                                                                                                            |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_job_version   | No              | String               | Version of the source training job. If the model is generated from a training job, specify this parameter for source tracing. If the model is imported from a third-party meta model, leave this parameter blank. By default, this parameter is left blank.                                                                                                       |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_type          | No              | String               | Model source type. Currently, the value can only be **auto**, which indicates an ExeML model (model download is not allowed). If the model is deployed by a training job, leave this parameter blank. By default, this parameter is left blank.                                                                                                                   |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_type           | Yes             | String               | Model type. The value can be **TensorFlow**, **MXNet**, **Spark_MLlib**, **Scikit_Learn**, **XGBoost**, **MindSpore**, **Image**, or **PyTorch**.                                                                                                                                                                                                                 |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | model_algorithm      | No              | String               | Model algorithm. If the algorithm has been configured in the model configuration file, this parameter can be left blank. For example, **predict_analysis**, **object_detection**, or **image_classification**.                                                                                                                                                    |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description          | No              | String               | Model description, which contains a maximum of 100 characters and cannot contain the following special characters: !<>=&'"                                                                                                                                                                                                                                        |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | execution_code       | No              | String               | OBS path to the execution script. The inference script must be stored in the **model** directory in the path where the model is located. For details, see the **source_location** parameter. The script name is fixed to **customize_service.py**.                                                                                                                |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | input_params         | No              | **params** array     | List of input parameters for model inference. By default, this parameter is left blank. If the **apis** information has been configured in the model configuration file, you do not need to set this parameter. The backend automatically reads the input parameters from the **apis** field in the configuration file.                                           |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | output_params        | No              | **params** array     | List of output parameters for model inference. By default, this parameter is left blank. If the **apis** information has been configured in the model configuration file, you do not need to set this parameter. The backend automatically reads the output parameters from the **apis** field in the configuration file.                                         |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dependencies         | No              | **dependency** array | Dependency package required for running the code and model. By default, this parameter is left blank. If the **dependencies** information has been configured in the model configuration file, you do not need to set this parameter. The backend automatically reads the dependencies to be installed from the **dependencies** field in the configuration file. |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | apis                 | No              | String               | List of inference APIs provided by a model. By default, this parameter is left blank. If the **apis** information has been configured in the model configuration file, you do not need to set this parameter. The backend automatically reads the configured inference API information from the **apis** field in the configuration file.                         |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** **params** parameters

   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                 |
   +============+===========+========+=============================================================================================================================+
   | url        | Yes       | String | Request path of a model inference API                                                                                       |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | param_name | Yes       | String | Parameter name, which contains a maximum of 64 characters                                                                   |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | param_type | Yes       | String | Basic parameter types of JSON schema, including **string**, **object**, **array**, **boolean**, **number**, and **integer** |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | min        | No        | Double | This parameter is optional when **param_type** is set to **int** or **float**. By default, this parameter is left blank.    |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | max        | No        | Double | This parameter is optional when **param_type** is set to **int** or **float**. By default, this parameter is left blank.    |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | param_desc | No        | String | Parameter description, which contains a maximum of 100 characters. By default, this parameter is left blank.                |
   +------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** **dependency** parameters

   +-----------+-----------+-------------------+-----------------------------------------------+
   | Parameter | Mandatory | Type              | Description                                   |
   +===========+===========+===================+===============================================+
   | installer | Yes       | String            | Installation mode. Only **pip** is supported. |
   +-----------+-----------+-------------------+-----------------------------------------------+
   | packages  | Yes       | **package** array | Collection of dependency packages             |
   +-----------+-----------+-------------------+-----------------------------------------------+

.. table:: **Table 5** **package** parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                    |
   +=================+=================+=================+================================================================================================================================+
   | package_name    | Yes             | String          | Name of a dependency package                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | package_version | No              | String          | Version of a dependency package                                                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+
   | restraint       | No              | String          | Version filtering condition. This parameter is mandatory only when **package_version** exists. Possible values are as follows: |
   |                 |                 |                 |                                                                                                                                |
   |                 |                 |                 | -  **EXACT**: the specified version                                                                                            |
   |                 |                 |                 | -  **ATLEAST**: not earlier than the specified version                                                                         |
   |                 |                 |                 | -  **ATMOST**: not later than the specified version                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 6** **create_model** response parameters

   +----------------+-----------+--------------+----------------------------------------------------------------------+
   | Parameter      | Mandatory | Type         | Description                                                          |
   +================+===========+==============+======================================================================+
   | model_instance | Yes       | Model object | Model object, which can be any of the APIs described in this chapter |
   +----------------+-----------+--------------+----------------------------------------------------------------------+

.. note::

   Example of creating a model in a handwritten digit recognition project using MXNet:

   ::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_instance = Model(session,
                             model_name = "digit recognition",
                             model_version = "1.0.0",
                             source_location = model_location,
                             model_type      = "MXNet",
                             model_algorithm = "image_classification")
