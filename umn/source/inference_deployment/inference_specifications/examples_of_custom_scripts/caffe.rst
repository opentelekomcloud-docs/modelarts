:original_name: inference-modelarts-0083.html

.. _inference-modelarts-0083:

Caffe
=====

Training and Saving a Model
---------------------------

**lenet_train_test.prototxt** file

::

   name: "LeNet"
   layer {
     name: "mnist"
     type: "Data"
     top: "data"
     top: "label"
     include {
       phase: TRAIN
     }
     transform_param {
       scale: 0.00390625
     }
     data_param {
       source: "examples/mnist/mnist_train_lmdb"
       batch_size: 64
       backend: LMDB
     }
   }
   layer {
     name: "mnist"
     type: "Data"
     top: "data"
     top: "label"
     include {
       phase: TEST
     }
     transform_param {
       scale: 0.00390625
     }
     data_param {
       source: "examples/mnist/mnist_test_lmdb"
       batch_size: 100
       backend: LMDB
     }
   }
   layer {
     name: "conv1"
     type: "Convolution"
     bottom: "data"
     top: "conv1"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     convolution_param {
       num_output: 20
       kernel_size: 5
       stride: 1
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "pool1"
     type: "Pooling"
     bottom: "conv1"
     top: "pool1"
     pooling_param {
       pool: MAX
       kernel_size: 2
       stride: 2
     }
   }
   layer {
     name: "conv2"
     type: "Convolution"
     bottom: "pool1"
     top: "conv2"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     convolution_param {
       num_output: 50
       kernel_size: 5
       stride: 1
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "pool2"
     type: "Pooling"
     bottom: "conv2"
     top: "pool2"
     pooling_param {
       pool: MAX
       kernel_size: 2
       stride: 2
     }
   }
   layer {
     name: "ip1"
     type: "InnerProduct"
     bottom: "pool2"
     top: "ip1"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     inner_product_param {
       num_output: 500
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "relu1"
     type: "ReLU"
     bottom: "ip1"
     top: "ip1"
   }
   layer {
     name: "ip2"
     type: "InnerProduct"
     bottom: "ip1"
     top: "ip2"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     inner_product_param {
       num_output: 10
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "accuracy"
     type: "Accuracy"
     bottom: "ip2"
     bottom: "label"
     top: "accuracy"
     include {
       phase: TEST
     }
   }
   layer {
     name: "loss"
     type: "SoftmaxWithLoss"
     bottom: "ip2"
     bottom: "label"
     top: "loss"
   }

**lenet_solver.prototxt** file

::

   # The train/test net protocol buffer definition
   net: "examples/mnist/lenet_train_test.prototxt"
   # test_iter specifies how many forward passes the test should carry out.
   # In the case of MNIST, we have test batch size 100 and 100 test iterations,
   # covering the full 10,000 testing images.
   test_iter: 100
   # Carry out testing every 500 training iterations.
   test_interval: 500
   # The base learning rate, momentum and the weight decay of the network.
   base_lr: 0.01
   momentum: 0.9
   weight_decay: 0.0005
   # The learning rate policy
   lr_policy: "inv"
   gamma: 0.0001
   power: 0.75
   # Display every 100 iterations
   display: 100
   # The maximum number of iterations
   max_iter: 1000
   # snapshot intermediate results
   snapshot: 5000
   snapshot_prefix: "examples/mnist/lenet"
   # solver mode: CPU or GPU
   solver_mode: CPU

Train the model.

.. code-block::

   ./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt

The **caffemodel** file is generated after model training. Rewrite the **lenet_train_test.prototxt** file to the **lenet_deploy.prototxt** file used for deployment by modifying input and output layers.

::

   name: "LeNet"
   layer {
     name: "data"
     type: "Input"
     top: "data"
     input_param { shape: { dim: 1 dim: 1  dim: 28 dim: 28 } }
   }
   layer {
     name: "conv1"
     type: "Convolution"
     bottom: "data"
     top: "conv1"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     convolution_param {
       num_output: 20
       kernel_size: 5
       stride: 1
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "pool1"
     type: "Pooling"
     bottom: "conv1"
     top: "pool1"
     pooling_param {
       pool: MAX
       kernel_size: 2
       stride: 2
     }
   }
   layer {
     name: "conv2"
     type: "Convolution"
     bottom: "pool1"
     top: "conv2"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     convolution_param {
       num_output: 50
       kernel_size: 5
       stride: 1
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "pool2"
     type: "Pooling"
     bottom: "conv2"
     top: "pool2"
     pooling_param {
       pool: MAX
       kernel_size: 2
       stride: 2
     }
   }
   layer {
     name: "ip1"
     type: "InnerProduct"
     bottom: "pool2"
     top: "ip1"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     inner_product_param {
       num_output: 500
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "relu1"
     type: "ReLU"
     bottom: "ip1"
     top: "ip1"
   }
   layer {
     name: "ip2"
     type: "InnerProduct"
     bottom: "ip1"
     top: "ip2"
     param {
       lr_mult: 1
     }
     param {
       lr_mult: 2
     }
     inner_product_param {
       num_output: 10
       weight_filler {
         type: "xavier"
       }
       bias_filler {
         type: "constant"
       }
     }
   }
   layer {
     name: "prob"
     type: "Softmax"
     bottom: "ip2"
     top: "prob"
   }

Inference Code
--------------

In the model inference code file **customize_service.py**, add a child model class which inherits properties from its parent model class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <en-us_topic_0000001910014882__en-us_topic_0172466150_table55021545175412>`.

::

   from model_service.caffe_model_service import CaffeBaseService

   import numpy as np

   import os, json

   import caffe

   from PIL import Image


   class LenetService(CaffeBaseService):

       def __init__(self, model_name, model_path):
           # Call the inference method of the parent class.
           super(LenetService, self).__init__(model_name, model_path)

           # Configure preprocessing information.
           transformer = caffe.io.Transformer({'data': self.net.blobs['data'].data.shape})
           # Transform to NCHW.
           transformer.set_transpose('data', (2, 0, 1))
           # Perform normalization.
           transformer.set_raw_scale('data', 255.0)

           # If the batch size is set to 1, inference is supported for only one image.
           self.net.blobs['data'].reshape(1, 1, 28, 28)
           self.transformer = transformer

          # Define the class labels.
           self.label = [0,1,2,3,4,5,6,7,8,9]


       def _preprocess(self, data):

           for k, v in data.items():
               for file_name, file_content in v.items():
                   im = caffe.io.load_image(file_content, color=False)
                  # Pre-process the images.
                   self.net.blobs['data'].data[...] = self.transformer.preprocess('data', im)

                   return

       def _postprocess(self, data):

           data = data['prob'][0, :]
           predicted = np.argmax(data)
           predicted = {"predicted" : str(predicted) }

           return predicted
