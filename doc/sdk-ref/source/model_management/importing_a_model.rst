:original_name: modelarts_04_0194.html

.. _modelarts_04_0194:

Importing a Model
=================

The model import function covers the following aspects:

-  Initialize the existing model and create a model object based on the model ID.
-  Create a model. For details about the attributes of the created model, see :ref:`Querying the Details About a Model <modelarts_04_0197>`.

Sample Model File
-----------------

Take a `custom PyTorch script <https://docs.otc.t-systems.com/modelarts/umn/examples_of_custom_scripts/pytorch.html#modelarts-23-0175>`__ as an example. Download `model.zip <https://obs-sdk.obs.eu-de.otc.t-systems.com/model.zip>`__ that can be directly deployed, decompress the package, and upload it to OBS. For details about the structure of the PyTorch model package, see `Model Package Specifications <https://docs.otc.t-systems.com/modelarts/umn/model_package_specifications/model_package_specifications.html>`__.

.. code-block::

   OBS bucket or directory name
   ├── resnet
   │   ├── model (Mandatory) Fixed subdirectory name. The subdirectory is used to store model-related files.
   │   │  ├──<<Custom Python package>> (Optional) Customized Python package, which can be directly referenced in model inference code
   │   │  ├──mnist_mlp.pt (Mandatory) PyTorch model file, which contains variable and weight information and is saved as state_dict
   │   │  ├──config.json (Mandatory) Model configuration file. The file name is fixed to config.json. Only one model configuration file is supported.
   │   │  ├──customize_service.py (Mandatory) Model inference code. The file name is fixed to customize_service.py. Only one model inference file is supported. The files on which customize_service.py depends can be directly stored in the model directory.

Sample Code
-----------

In ModelArts notebook, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

::

   from modelarts.session import Session
   from modelarts.model import Model
   from modelarts.config.model_config import ServiceConfig, Params, Dependencies, Packages

   session = Session()

-  Method 1: Initialize an existing model.

   ::

      model_instance = Model(session, model_id="your_model_id")

-  Method 2: Create a model.

   ::

      model_location = "/your_obs_bucket/model_path"            # Change to the OBS path to the model file
      execution_code = "/your_obs_bucket/model_path/customize_service.py"
      runtime = "python3.7"

      model_instance = Model(
                              session,
                              model_name="input_model_name",    #  (Optional) Model name
                              model_version="1.0.0",            # (Optional) Model version
                              source_location=model_location,   # OBS path to the model file, for example, /your_obs_bucket/model_path
                              model_type="PyTorch",             # Model type
                              execution_code=execution_code,    # (Optional) OBS path to the execution script, for example, /your_obs_bucket/model_path/customize_service.py
                              runtime = runtime                 # (Optional) Supported runtime environment
                             )

   .. note::

      **dependencies** will overwrite the data in **config.json** in the preceding example. You do not need to use **dependencies**. The following section describes the **dependencies** formats.

   -  Definition formats of the **dependencies** parameter group used in method 2

      The SDK provides the definition of the **dependencies** parameter group. The type of **dependencies** is list, and those of the tuple objects in the list are Dependencies.

      The code is as follows:

      ::

         dependencies = []
         dependency1 = Dependencies(
                 installer="pip",                # Installation mode. pip is supported.
                 packages=packages               # Collection of dependency packages. For details, see packages.
                 )
         dependencies.append(dependency1)

   -  Definition formats of the **package** parameter group used in method 2

      The SDK provides the definition of the **packages** parameter group. The type of **packages** is list, and those of the tuple objects in the list are Packages.

      The code is as follows:

      ::

         packages = []
         package1 = Packages(
             package_name="package_name",       # Package name
             package_version="version",         # Package version
             restraint="EXACT")
         packages.append(package1)

      .. note::

         The following is an example of creating a **dependencies** parameter group:

         .. code-block::

            dependencies = []
            packages = [{
                "package_name": "numpy",
                "package_version": "1.15.0",
                "restraint": "EXACT"
                }, {
                    "package_name": "h5py",
                    "package_version": "2.8.0",
                    "restraint": "EXACT"
                }]
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
   | execution_code       | No              | String               | OBS path to the script to be executed. If **customize_service.py** is not output by the model, configure this parameter to specify the path. The inference script must be stored in the **model** directory in the path where the model is located. For details, see the **source_location** parameter. The script name is fixed to **customize_service.py**.     |
   +----------------------+-----------------+----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | runtime              | No              | String               | Supported runtime environment. This parameter is mandatory if **model_type** is used. The **runtime** parameter varies depending on engines. For details, see `Supported AI engines and their runtime <https://docs.otc.t-systems.com/modelarts/umn/model_management/importing_a_model/importing_a_meta_model_from_obs.html#modelarts-23-0207>`__.                |
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
                             model_name="digit_recognition",
                             model_version="1.0.0",
                             source_location=model_location,
                             model_type="MXNet",
                             model_algorithm="image_classification"
                             )
