:original_name: develop-modelarts-0023.html

.. _develop-modelarts-0023:

Resumable Training and Incremental Training
===========================================

Overview
--------

Resumable training indicates that an interrupted training job can be automatically resumed from the checkpoint where the previous training was interrupted. This method is applicable to model training that takes a long time.

Incremental training is a method in which input data is continuously used to extend the existing model's knowledge to further train the model.

Checkpoints are used to resume model training or incrementally train a model.

During model training, training results (including but not limited to epochs, model weights, optimizer status, and scheduler status) are continuously saved. In this way, an interrupted training job can be automatically resumed from the checkpoint where the previous training was interrupted.

To resume a training job, load a checkpoint and use the checkpoint information to initialize the training status. To do so, add reload ckpt to the code.

Resumable Training and Incremental Training in ModelArts
--------------------------------------------------------

To resume model training or incrementally train a model in ModelArts, configure **Training Output**.

When creating a training job, configure the data path to the training output, save checkpoints in this data path, and set **Predownload** to **Yes**. If you set **Predownload** to **Yes**, the system automatically downloads the **checkpoint** file in the training output data path to a local directory of the training container before the training job is started.


.. figure:: /_static/images/en-us_image_0000002079098061.png
   :alt: **Figure 1** Training Output

   **Figure 1** Training Output

Enable fault tolerance check (auto restart) for resumable training. On the training job creation page, enable **Auto Restart**. If the environment pre-check fails, the hardware is not functional, or the training job fails, ModelArts will automatically issue the training job again.


.. figure:: /_static/images/en-us_image_0000002043177360.png
   :alt: **Figure 2** Auto Restart

   **Figure 2** Auto Restart

reload ckpt for MindSpore
-------------------------

.. code-block::

   import os
   import argparse
   parser.add_argument("--train_url", type=str)
   args = parser.parse_known_args()
   # train_url is set to /home/ma-user/modelarts/outputs/train_url_0.
   train_url = args.train_url

   # Initially defined network, loss function, and optimizer
   net = resnet50(args_opt.batch_size, args_opt.num_classes)
   ls = SoftmaxCrossEntropyWithLogits(sparse=True, reduction="mean")
   opt = Momentum(filter(lambda x: x.requires_grad, net.get_parameters()), 0.01, 0.9)
   # Initial epoch value for the first training. The initial value of epoch_size will be customized in MindSpore 1.3 and later versions.
   # cur_epoch_num = 0
   # Check whether there is a model file in the OBS output path. If there is no file, the model will be trained from the beginning by default. If there is a model file, the CKPT file with the maximum epoch value will be loaded as the pre-trained model.
   if os.listdir(train_url):
       last_ckpt = sorted([file for file in os.listdir(train_url) if file.endswith(".ckpt")])[-1]
       print('last_ckpt:', last_ckpt)
       last_ckpt_file = os.path.join(train_url, last_ckpt)
       # Load the checkpoint.
       param_dict = load_checkpoint(last_ckpt_file)
       print('> load last ckpt and continue training!!')
       # Load model parameters to the network.
       load_param_into_net(net, param_dict)
       # Load model parameters to the optimizer.
       load_param_into_net(opt, param_dict)

       # Obtain the saved epoch value. The model will continue to be trained based on the epoch value. This function will be supported in MindSpore 1.3 and later versions.
       # if param_dict.get("epoch_num"):
       #     cur_epoch_num = int(param_dict["epoch_num"].data.asnumpy())
   model = Model(net, loss_fn=ls, optimizer=opt, metrics={'acc'})
   # as for train, users could use model.train
   if args_opt.do_train:
       dataset = create_dataset()
       batch_num = dataset.get_dataset_size()
       config_ck = CheckpointConfig(save_checkpoint_steps=batch_num,
                                        keep_checkpoint_max=35)
       # For append_info=[{"epoch_num": cur_epoch_num}], append_info will be supported in MindSpore 1.3 and later versions to save the epoch value at the current time.
       ckpoint_cb = ModelCheckpoint(prefix="train_resnet_cifar10",
                                        directory=args_opt.train_url,
                                        config=config_ck)
       loss_cb = LossMonitor()
       model.train(epoch_size, dataset, callbacks=[ckpoint_cb, loss_cb])
       # For model.train(epoch_size-cur_epoch_num, dataset, callbacks=[ckpoint_cb, loss_cb]), the training resumed from the breakpoint will be supported in MindSpore 1.3 and later versions.
