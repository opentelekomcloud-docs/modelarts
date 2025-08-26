:original_name: modelarts_05_0076.html

.. _modelarts_05_0076:

How Do I Perform Incremental Training When Using MoXing?
========================================================

If you are not satisfied with training results when using MoXing to build a model, you can perform incremental training after modifying some data and label information.

Adding Incremental Training Parameters to **mox.run**
-----------------------------------------------------

After modifying labeling data or datasets, you can modify the **log_dir** parameter in and add the **checkpoint_path** parameter to **mox.run**. Set **log_dir** to a new directory and **checkpoint_path** to the output path of the previous training results. If the output path is an OBS directory, set the path to a value starting with **obs://**.

If labels are changed for label data, perform operations in :ref:`If Labels Are Changed <en-us_topic_0000002374726653__section432681405612>` before running **mox.run**.

.. code-block::

     mox.run(input_fn=input_fn,
             model_fn=model_fn,
             optimizer_fn=optimizer_fn,
             run_mode=flags.run_mode,
             inter_mode=mox.ModeKeys.EVAL if use_eval_data else None,
             log_dir=log_dir,
             batch_size=batch_size_per_device,
             auto_batch=False,
             max_number_of_steps=max_number_of_steps,
             log_every_n_steps=flags.log_every_n_steps,
             save_summary_steps=save_summary_steps,
             save_model_secs=save_model_secs,
             checkpoint_path=flags.checkpoint_url,
             export_model=mox.ExportKeys.TF_SERVING)

.. _en-us_topic_0000002374726653__section432681405612:

If Labels Are Changed
---------------------

If the labels in a dataset have changed, execute the following statement. The statement must be executed before running **mox.run**.

In the statement, the **logits** variable indicates classification layer weights in different networks, and different parameters are configured. Set this parameter to the corresponding keyword.

.. code-block::

   mox.set_flag('checkpoint_exclude_patterns', 'logits')

If the built-in network of MoXing is used, the corresponding keyword needs to be obtained by calling the following API. In this example, the **Resnet_v1_50** keyword is the value of **logits**.

.. code-block::

   import moxing.tensorflow as mox

   model_meta = mox.get_model_meta(mox.NetworkKeys.RESNET_V1_50)
   logits_pattern = model_meta.default_logits_pattern
   print(logits_pattern)

You can also obtain a list of networks supported by MoXing by calling the following API:

.. code-block::

   import moxing.tensorflow as mox
   print(help(mox.NetworkKeys))

The following information is displayed:

.. code-block::

   Help on class NetworkKeys in module
   moxing.tensorflow.nets.nets_factory:

   class NetworkKeys(builtins.object)
    |  Data descriptors defined here:
    |
    |  __dict__
    |      dictionary for instance variables (if defined)
    |
    |  __weakref__
    |      list of weak references to the object (if defined)
    |
    |  ----------------------------------------------------------------------
    |  Data and other attributes defined here:
    |
    |  ALEXNET_V2 = 'alexnet_v2'
    |
    |  CIFARNET = 'cifarnet'
    |
    |  INCEPTION_RESNET_V2 = 'inception_resnet_v2'
    |
    |  INCEPTION_V1 = 'inception_v1'
    |
    |  INCEPTION_V2 = 'inception_v2'
    |
    |  INCEPTION_V3 = 'inception_v3'
    |
    |  INCEPTION_V4 = 'inception_v4'
    |
    |  LENET = 'lenet'
    |
    |  MOBILENET_V1 = 'mobilenet_v1'
    |
    |  MOBILENET_V1_025 = 'mobilenet_v1_025'
    |
    |  MOBILENET_V1_050 = 'mobilenet_v1_050'
    |
    |  MOBILENET_V1_075 = 'mobilenet_v1_075'
    |
    |  MOBILENET_V2 = 'mobilenet_v2'
    |
    |  MOBILENET_V2_035 = 'mobilenet_v2_035'
    |
    |  MOBILENET_V2_140 = 'mobilenet_v2_140'
    |
    |  NASNET_CIFAR = 'nasnet_cifar'
    |
    |  NASNET_LARGE = 'nasnet_large'
    |
    |  NASNET_MOBILE = 'nasnet_mobile'
    |
    |  OVERFEAT = 'overfeat'
    |
    |  PNASNET_LARGE = 'pnasnet_large'
    |
    |  PNASNET_MOBILE = 'pnasnet_mobile'
    |
    |  PVANET = 'pvanet'
    |
    |  RESNET_V1_101 = 'resnet_v1_101'
    |
    |  RESNET_V1_110 = 'resnet_v1_110'
    |
    |  RESNET_V1_152 = 'resnet_v1_152'
    |
    |  RESNET_V1_18 = 'resnet_v1_18'
    |
    |  RESNET_V1_20 = 'resnet_v1_20'
    |
    |  RESNET_V1_200 = 'resnet_v1_200'
    |
    |  RESNET_V1_50 = 'resnet_v1_50'
    |
    |  RESNET_V1_50_8K = 'resnet_v1_50_8k'
    |
    |  RESNET_V1_50_MOX = 'resnet_v1_50_mox'
    |
    |  RESNET_V1_50_OCT = 'resnet_v1_50_oct'
    |
    |  RESNET_V2_101 = 'resnet_v2_101'
    |
    |  RESNET_V2_152 = 'resnet_v2_152'
    |
    |  RESNET_V2_200 = 'resnet_v2_200'
    |
    |  RESNET_V2_50 = 'resnet_v2_50'
    |
    |  RESNEXT_B_101 = 'resnext_b_101'
    |
    |  RESNEXT_B_50 = 'resnext_b_50'
    |
    |  RESNEXT_C_101 = 'resnext_c_101'
    |
    |  RESNEXT_C_50 = 'resnext_c_50'
    |
    |  VGG_16 = 'vgg_16'
    |
    |  VGG_16_BN = 'vgg_16_bn'
    |
    |  VGG_19 = 'vgg_19'
    |
    |  VGG_19_BN = 'vgg_19_bn'
    |
    |  VGG_A = 'vgg_a'
    |
    |  VGG_A_BN = 'vgg_a_bn'
    |
    |  XCEPTION_41 = 'xception_41'
    |
    |  XCEPTION_65 = 'xception_65'
    |
    |  XCEPTION_71 = 'xception_71'
