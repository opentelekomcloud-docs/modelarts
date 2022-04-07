.. _modelarts_23_0107:

Compressing and Converting Models
=================================

To obtain higher computing power, you can deploy the models created on ModelArts or a local PC on the Ascend chip, Arm, or GPU. In this case, you need to compress or convert the models to the required formats before deploying them.

ModelArts supports model conversion, allowing you to convert a model to a required format before deploying the model on a chip with higher computing power and performance.

Model conversion applies to the following scenarios:

-  If you use the TensorFlow framework (in **frozen_graph** or **saved_model** format) to train a model, you can convert the model to the **.om** format. The converted model can be deployed and run on Ascend chips.

Constraints
-----------

-  Only Ascend chips are supported for model conversion.
-  Only Caffe and TensorFlow models can be converted. For a TensorFlow model, the input data type is of the INT32, BOOL, UINT8, or FLOAT type.
-  ModelArts provides conversion templates for you to choose. For details about the supported templates, see :ref:`Conversion Templates <modelarts_23_0110>`.
-  The **.tflite** and TensorRT formats support fewer operators and quantization operators. Therefore, some models may fail to be converted. If the conversion fails, view the log dialog box or check error logs in the conversion output directory.
-  An OBS directory must be specified in compression/conversion tasks. Ensure that the OBS directory you use and ModelArts are in the same region.
-  When importing the converted model to ModelArts, you need to use the :ref:`model template <modelarts_23_0205>`.
-  For a TensorFlow model, the FrozenGraphDef and SavedModel formats are supported. If a model is in the SavedModel format, the model is converted to the FrozenGraphDef format and then to the OM format.
-  Inputs with dynamic shapes are not supported, for example, NHWC = [?,?,?,3]. A fixed value needs to be specified during model conversion.
-  The input can be up to 4-dimensional. Operators involving dimension changes (such as reshape and expanddim) cannot output five dimensions.
-  Except the const operator, the input and output at all layers in a model must meet the condition **dim!=0**.
-  Model conversion does not support models that contain training operators.
-  A UINT8 quantized model cannot be converted.
-  Model operators support only 2D convolution but do not support 3D convolution. The batch_normalization_1 and FusedBatchNorm operators cannot be converted in batches.

Deleting a Model Compression/Conversion Task
--------------------------------------------

You can delete unnecessary conversion tasks. However, tasks in the **Running** or **Initializing** status cannot be deleted.

.. note::

   Deleted tasks cannot be recovered. Exercise caution when performing this operation.

-  Deleting a single task:

   On the **Compression/Conversion** page, click **Delete** in the **Operation** column of the target task.

-  Deleting a batch of tasks:

   On the **Compression/Conversion** page, select multiple tasks to be deleted and click **Delete** in the upper left corner.
