:original_name: modelarts_05_0091.html

.. _modelarts_05_0091:

How Do I Load Some Well Trained Parameters During Job Training?
===============================================================

During job training, some parameters need to be loaded from a pre-trained model to initialize the current model. You can use the following methods to load the parameters:

#. View all parameters by using the following code.

   .. code-block::

      from moxing.tensorflow.utils.hyper_param_flags import mox_flags
      print(mox_flags.get_help())

#. Specify the parameters to be restored during model loading. **checkpoint_include_patterns** is the parameter that needs to be restored, and **checkpoint_exclude_patterns** is the parameter that does not need to be restored.

   .. code-block::

      checkpoint_include_patterns: Variables names patterns to include when restoring checkpoint. Such as: conv2d/weights.
      checkpoint_exclude_patterns: Variables names patterns to include when restoring checkpoint. Such as: conv2d/weights.

#. Specify a list of parameters to be trained. **trainable_include_patterns** is a list of parameters that need to be trained, and **trainable_exclude_patterns** is a list of parameters that do not need to be trained.

   .. code-block::

      --trainable_exclude_patterns: Variables names patterns to exclude for trainable variables. Such as: conv1,conv2.
      --trainable_include_patterns: Variables names patterns to include for trainable variables. Such as: logits.
