:original_name: modelarts_05_0502.html

.. _modelarts_05_0502:

What Do I Do If an Image Error Occurred During Model Training Using ExeML?
==========================================================================

If an image classification or object detection algorithm of ExeML is used, after the labeled data is trained, the training result is an image error. :ref:`Table 1 <modelarts_05_0502__table740413332320>` lists solutions to different errors.

.. _modelarts_05_0502__table740413332320:

.. table:: **Table 1** Image errors in image classification and object detection of ExeML

   +-----+------------------+--------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------+
   | No. | Error Parameter  | Error Description                                      | Solution Parameter | Solution Description                                                                            |
   +=====+==================+========================================================+====================+=================================================================================================+
   | 1   | load failed      | The image cannot be decoded or restored.               | ignore             | The system has ignored this image. No manual operation is required.                             |
   +-----+------------------+--------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------+
   | 2   | tf-decode failed | The image cannot be decoded by TensorFlow or restored. | ignore             | The system has ignored this image. No manual operation is required.                             |
   +-----+------------------+--------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------+
   | 3   | size over        | The image size exceeded 5 MB.                          | resize to small    | The system has compressed the image size to be less than 5 MB. No manual operation is required. |
   +-----+------------------+--------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------+
   | 4   | mode illegal     | The image is not in RGB format.                        | convert to rgb     | The system has converted the image to the RGB format. No manual operation is required.          |
   +-----+------------------+--------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------+
   | 5   | type illegal     | The file is not an image but can be converted to JPG.  | convert to jpg     | The system has converted the image to the JPG format. No manual operation is required.          |
   +-----+------------------+--------------------------------------------------------+--------------------+-------------------------------------------------------------------------------------------------+
