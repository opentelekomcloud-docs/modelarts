.. _modelarts_23_0109:

Model Output Path Description
=============================

Ascend Chip
-----------

The following describes the output path of the model run on the Ascend chip after conversion:

-  For TensorFlow-based models, the output path must comply with the following specifications during model conversion:

   .. code-block::

      |
      |---xxxx.om           Converted model to run on the Ascend chip. The model file name extension is .om.
      |---job_log.txt       Conversion log file
