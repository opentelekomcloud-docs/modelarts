.. _modelarts_23_0108:

Model Input Path Specifications
===============================

Ascend Chip
-----------

The requirements for converting the models run on the Ascend chip are as follows:

-  For TensorFlow-based models (in **frozen_graph** or **saved_model** format), the input path must comply with the following specifications during model conversion:

   **frozen_graph** format

   .. code-block::

      |
      |---xxxx.pb                 (Mandatory) Model network file. Only one model network file can exist in the input path. The model must be in frozen_graph or saved_model format.
      |---insert_op_conf.cfg      (Optional) Insertion operator configuration file. Only one insertion operator configuration file can exist in the input path.
      |---plugin                  (Optional) Custom operator directory. The input directory can contain only one plugin folder. Only custom operators developed based on Tensor Engine (TE) are supported.

   **saved_model** format

   .. code-block::

      |
      |---saved_model.pb          (Mandatory) Model network file. Only one model network file can exist in the input path. The model must be in frozen_graph or saved_model format.
      |---variables               (Mandatory) Fixed subdirectory name, including the model weight deviation.
          |---variables.index     Mandatory
          |---variables.data-00000-of-00001 Mandatory
      |---insert_op_conf.cfg      (Optional) Insertion operator configuration file. Only one insertion operator configuration file can exist in the input path.
      |---plugin                  (Optional) Custom operator directory. The input directory can contain only one plugin folder. Only custom operators developed based on Tensor Engine (TE) are supported.
