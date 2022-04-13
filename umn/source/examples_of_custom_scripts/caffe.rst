.. _modelarts_23_0176:

Caffe
=====

Training and Saving a Model
---------------------------

**lenet_train_test.prototxt** file

+-----------------------------------+--------------------------------------------------+
| ::                                | ::                                               |
|                                   |                                                  |
|      1                            |    name: "LeNet"                                 |
|      2                            |    layer {                                       |
|      3                            |      name: "mnist"                               |
|      4                            |      type: "Data"                                |
|      5                            |      top: "data"                                 |
|      6                            |      top: "label"                                |
|      7                            |      include {                                   |
|      8                            |        phase: TRAIN                              |
|      9                            |      }                                           |
|     10                            |      transform_param {                           |
|     11                            |        scale: 0.00390625                         |
|     12                            |      }                                           |
|     13                            |      data_param {                                |
|     14                            |        source: "examples/mnist/mnist_train_lmdb" |
|     15                            |        batch_size: 64                            |
|     16                            |        backend: LMDB                             |
|     17                            |      }                                           |
|     18                            |    }                                             |
|     19                            |    layer {                                       |
|     20                            |      name: "mnist"                               |
|     21                            |      type: "Data"                                |
|     22                            |      top: "data"                                 |
|     23                            |      top: "label"                                |
|     24                            |      include {                                   |
|     25                            |        phase: TEST                               |
|     26                            |      }                                           |
|     27                            |      transform_param {                           |
|     28                            |        scale: 0.00390625                         |
|     29                            |      }                                           |
|     30                            |      data_param {                                |
|     31                            |        source: "examples/mnist/mnist_test_lmdb"  |
|     32                            |        batch_size: 100                           |
|     33                            |        backend: LMDB                             |
|     34                            |      }                                           |
|     35                            |    }                                             |
|     36                            |    layer {                                       |
|     37                            |      name: "conv1"                               |
|     38                            |      type: "Convolution"                         |
|     39                            |      bottom: "data"                              |
|     40                            |      top: "conv1"                                |
|     41                            |      param {                                     |
|     42                            |        lr_mult: 1                                |
|     43                            |      }                                           |
|     44                            |      param {                                     |
|     45                            |        lr_mult: 2                                |
|     46                            |      }                                           |
|     47                            |      convolution_param {                         |
|     48                            |        num_output: 20                            |
|     49                            |        kernel_size: 5                            |
|     50                            |        stride: 1                                 |
|     51                            |        weight_filler {                           |
|     52                            |          type: "xavier"                          |
|     53                            |        }                                         |
|     54                            |        bias_filler {                             |
|     55                            |          type: "constant"                        |
|     56                            |        }                                         |
|     57                            |      }                                           |
|     58                            |    }                                             |
|     59                            |    layer {                                       |
|     60                            |      name: "pool1"                               |
|     61                            |      type: "Pooling"                             |
|     62                            |      bottom: "conv1"                             |
|     63                            |      top: "pool1"                                |
|     64                            |      pooling_param {                             |
|     65                            |        pool: MAX                                 |
|     66                            |        kernel_size: 2                            |
|     67                            |        stride: 2                                 |
|     68                            |      }                                           |
|     69                            |    }                                             |
|     70                            |    layer {                                       |
|     71                            |      name: "conv2"                               |
|     72                            |      type: "Convolution"                         |
|     73                            |      bottom: "pool1"                             |
|     74                            |      top: "conv2"                                |
|     75                            |      param {                                     |
|     76                            |        lr_mult: 1                                |
|     77                            |      }                                           |
|     78                            |      param {                                     |
|     79                            |        lr_mult: 2                                |
|     80                            |      }                                           |
|     81                            |      convolution_param {                         |
|     82                            |        num_output: 50                            |
|     83                            |        kernel_size: 5                            |
|     84                            |        stride: 1                                 |
|     85                            |        weight_filler {                           |
|     86                            |          type: "xavier"                          |
|     87                            |        }                                         |
|     88                            |        bias_filler {                             |
|     89                            |          type: "constant"                        |
|     90                            |        }                                         |
|     91                            |      }                                           |
|     92                            |    }                                             |
|     93                            |    layer {                                       |
|     94                            |      name: "pool2"                               |
|     95                            |      type: "Pooling"                             |
|     96                            |      bottom: "conv2"                             |
|     97                            |      top: "pool2"                                |
|     98                            |      pooling_param {                             |
|     99                            |        pool: MAX                                 |
|    100                            |        kernel_size: 2                            |
|    101                            |        stride: 2                                 |
|    102                            |      }                                           |
|    103                            |    }                                             |
|    104                            |    layer {                                       |
|    105                            |      name: "ip1"                                 |
|    106                            |      type: "InnerProduct"                        |
|    107                            |      bottom: "pool2"                             |
|    108                            |      top: "ip1"                                  |
|    109                            |      param {                                     |
|    110                            |        lr_mult: 1                                |
|    111                            |      }                                           |
|    112                            |      param {                                     |
|    113                            |        lr_mult: 2                                |
|    114                            |      }                                           |
|    115                            |      inner_product_param {                       |
|    116                            |        num_output: 500                           |
|    117                            |        weight_filler {                           |
|    118                            |          type: "xavier"                          |
|    119                            |        }                                         |
|    120                            |        bias_filler {                             |
|    121                            |          type: "constant"                        |
|    122                            |        }                                         |
|    123                            |      }                                           |
|    124                            |    }                                             |
|    125                            |    layer {                                       |
|    126                            |      name: "relu1"                               |
|    127                            |      type: "ReLU"                                |
|    128                            |      bottom: "ip1"                               |
|    129                            |      top: "ip1"                                  |
|    130                            |    }                                             |
|    131                            |    layer {                                       |
|    132                            |      name: "ip2"                                 |
|    133                            |      type: "InnerProduct"                        |
|    134                            |      bottom: "ip1"                               |
|    135                            |      top: "ip2"                                  |
|    136                            |      param {                                     |
|    137                            |        lr_mult: 1                                |
|    138                            |      }                                           |
|    139                            |      param {                                     |
|    140                            |        lr_mult: 2                                |
|    141                            |      }                                           |
|    142                            |      inner_product_param {                       |
|    143                            |        num_output: 10                            |
|    144                            |        weight_filler {                           |
|    145                            |          type: "xavier"                          |
|    146                            |        }                                         |
|    147                            |        bias_filler {                             |
|    148                            |          type: "constant"                        |
|    149                            |        }                                         |
|    150                            |      }                                           |
|    151                            |    }                                             |
|    152                            |    layer {                                       |
|    153                            |      name: "accuracy"                            |
|    154                            |      type: "Accuracy"                            |
|    155                            |      bottom: "ip2"                               |
|    156                            |      bottom: "label"                             |
|    157                            |      top: "accuracy"                             |
|    158                            |      include {                                   |
|    159                            |        phase: TEST                               |
|    160                            |      }                                           |
|    161                            |    }                                             |
|    162                            |    layer {                                       |
|    163                            |      name: "loss"                                |
|    164                            |      type: "SoftmaxWithLoss"                     |
|    165                            |      bottom: "ip2"                               |
|    166                            |      bottom: "label"                             |
|    167                            |      top: "loss"                                 |
|    168                            |    }                                             |
+-----------------------------------+--------------------------------------------------+

**lenet_solver.prototxt** file

+-----------------------------------+---------------------------------------------------------------------------------+
| ::                                | ::                                                                              |
|                                   |                                                                                 |
|     1                             |    # The train/test net protocol buffer definition                              |
|     2                             |    net: "examples/mnist/lenet_train_test.prototxt"                              |
|     3                             |    # test_iter specifies how many forward passes the test should carry out.     |
|     4                             |    # In the case of MNIST, we have test batch size 100 and 100 test iterations, |
|     5                             |    # covering the full 10,000 testing images.                                   |
|     6                             |    test_iter: 100                                                               |
|     7                             |    # Carry out testing every 500 training iterations.                           |
|     8                             |    test_interval: 500                                                           |
|     9                             |    # The base learning rate, momentum and the weight decay of the network.      |
|    10                             |    base_lr: 0.01                                                                |
|    11                             |    momentum: 0.9                                                                |
|    12                             |    weight_decay: 0.0005                                                         |
|    13                             |    # The learning rate policy                                                   |
|    14                             |    lr_policy: "inv"                                                             |
|    15                             |    gamma: 0.0001                                                                |
|    16                             |    power: 0.75                                                                  |
|    17                             |    # Display every 100 iterations                                               |
|    18                             |    display: 100                                                                 |
|    19                             |    # The maximum number of iterations                                           |
|    20                             |    max_iter: 1000                                                               |
|    21                             |    # snapshot intermediate results                                              |
|    22                             |    snapshot: 5000                                                               |
|    23                             |    snapshot_prefix: "examples/mnist/lenet"                                      |
|    24                             |    # solver mode: CPU or GPU                                                    |
|    25                             |    solver_mode: CPU                                                             |
+-----------------------------------+---------------------------------------------------------------------------------+

Train the model.

.. code-block::

   ./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt

The **caffemodel** file is generated after model training. Rewrite the **lenet_train_test.prototxt** file to the **lenet_deploy.prototxt** file used for deployment by modifying input and output layers.

+-----------------------------------+-----------------------------------------------------------------+
| ::                                | ::                                                              |
|                                   |                                                                 |
|      1                            |    name: "LeNet"                                                |
|      2                            |    layer {                                                      |
|      3                            |      name: "data"                                               |
|      4                            |      type: "Input"                                              |
|      5                            |      top: "data"                                                |
|      6                            |      input_param { shape: { dim: 1 dim: 1  dim: 28 dim: 28 } }  |
|      7                            |    }                                                            |
|      8                            |    layer {                                                      |
|      9                            |      name: "conv1"                                              |
|     10                            |      type: "Convolution"                                        |
|     11                            |      bottom: "data"                                             |
|     12                            |      top: "conv1"                                               |
|     13                            |      param {                                                    |
|     14                            |        lr_mult: 1                                               |
|     15                            |      }                                                          |
|     16                            |      param {                                                    |
|     17                            |        lr_mult: 2                                               |
|     18                            |      }                                                          |
|     19                            |      convolution_param {                                        |
|     20                            |        num_output: 20                                           |
|     21                            |        kernel_size: 5                                           |
|     22                            |        stride: 1                                                |
|     23                            |        weight_filler {                                          |
|     24                            |          type: "xavier"                                         |
|     25                            |        }                                                        |
|     26                            |        bias_filler {                                            |
|     27                            |          type: "constant"                                       |
|     28                            |        }                                                        |
|     29                            |      }                                                          |
|     30                            |    }                                                            |
|     31                            |    layer {                                                      |
|     32                            |      name: "pool1"                                              |
|     33                            |      type: "Pooling"                                            |
|     34                            |      bottom: "conv1"                                            |
|     35                            |      top: "pool1"                                               |
|     36                            |      pooling_param {                                            |
|     37                            |        pool: MAX                                                |
|     38                            |        kernel_size: 2                                           |
|     39                            |        stride: 2                                                |
|     40                            |      }                                                          |
|     41                            |    }                                                            |
|     42                            |    layer {                                                      |
|     43                            |      name: "conv2"                                              |
|     44                            |      type: "Convolution"                                        |
|     45                            |      bottom: "pool1"                                            |
|     46                            |      top: "conv2"                                               |
|     47                            |      param {                                                    |
|     48                            |        lr_mult: 1                                               |
|     49                            |      }                                                          |
|     50                            |      param {                                                    |
|     51                            |        lr_mult: 2                                               |
|     52                            |      }                                                          |
|     53                            |      convolution_param {                                        |
|     54                            |        num_output: 50                                           |
|     55                            |        kernel_size: 5                                           |
|     56                            |        stride: 1                                                |
|     57                            |        weight_filler {                                          |
|     58                            |          type: "xavier"                                         |
|     59                            |        }                                                        |
|     60                            |        bias_filler {                                            |
|     61                            |          type: "constant"                                       |
|     62                            |        }                                                        |
|     63                            |      }                                                          |
|     64                            |    }                                                            |
|     65                            |    layer {                                                      |
|     66                            |      name: "pool2"                                              |
|     67                            |      type: "Pooling"                                            |
|     68                            |      bottom: "conv2"                                            |
|     69                            |      top: "pool2"                                               |
|     70                            |      pooling_param {                                            |
|     71                            |        pool: MAX                                                |
|     72                            |        kernel_size: 2                                           |
|     73                            |        stride: 2                                                |
|     74                            |      }                                                          |
|     75                            |    }                                                            |
|     76                            |    layer {                                                      |
|     77                            |      name: "ip1"                                                |
|     78                            |      type: "InnerProduct"                                       |
|     79                            |      bottom: "pool2"                                            |
|     80                            |      top: "ip1"                                                 |
|     81                            |      param {                                                    |
|     82                            |        lr_mult: 1                                               |
|     83                            |      }                                                          |
|     84                            |      param {                                                    |
|     85                            |        lr_mult: 2                                               |
|     86                            |      }                                                          |
|     87                            |      inner_product_param {                                      |
|     88                            |        num_output: 500                                          |
|     89                            |        weight_filler {                                          |
|     90                            |          type: "xavier"                                         |
|     91                            |        }                                                        |
|     92                            |        bias_filler {                                            |
|     93                            |          type: "constant"                                       |
|     94                            |        }                                                        |
|     95                            |      }                                                          |
|     96                            |    }                                                            |
|     97                            |    layer {                                                      |
|     98                            |      name: "relu1"                                              |
|     99                            |      type: "ReLU"                                               |
|    100                            |      bottom: "ip1"                                              |
|    101                            |      top: "ip1"                                                 |
|    102                            |    }                                                            |
|    103                            |    layer {                                                      |
|    104                            |      name: "ip2"                                                |
|    105                            |      type: "InnerProduct"                                       |
|    106                            |      bottom: "ip1"                                              |
|    107                            |      top: "ip2"                                                 |
|    108                            |      param {                                                    |
|    109                            |        lr_mult: 1                                               |
|    110                            |      }                                                          |
|    111                            |      param {                                                    |
|    112                            |        lr_mult: 2                                               |
|    113                            |      }                                                          |
|    114                            |      inner_product_param {                                      |
|    115                            |        num_output: 10                                           |
|    116                            |        weight_filler {                                          |
|    117                            |          type: "xavier"                                         |
|    118                            |        }                                                        |
|    119                            |        bias_filler {                                            |
|    120                            |          type: "constant"                                       |
|    121                            |        }                                                        |
|    122                            |      }                                                          |
|    123                            |    }                                                            |
|    124                            |    layer {                                                      |
|    125                            |      name: "prob"                                               |
|    126                            |      type: "Softmax"                                            |
|    127                            |      bottom: "ip2"                                              |
|    128                            |      top: "prob"                                                |
|    129                            |    }                                                            |
+-----------------------------------+-----------------------------------------------------------------+

Inference Code
--------------

+-----------------------------------+-----------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                            |
|                                   |                                                                                               |
|     1                             |    from model_service.caffe_model_service import CaffeBaseService                             |
|     2                             |                                                                                               |
|     3                             |    import numpy as np                                                                         |
|     4                             |                                                                                               |
|     5                             |    import os, json                                                                            |
|     6                             |                                                                                               |
|     7                             |    import caffe                                                                               |
|     8                             |                                                                                               |
|     9                             |    from PIL import Image                                                                      |
|    10                             |                                                                                               |
|    11                             |                                                                                               |
|    12                             |    class LenetService(CaffeBaseService):                                                      |
|    13                             |                                                                                               |
|    14                             |        def __init__(self, model_name, model_path):                                            |
|    15                             |            # Call the inference method of the parent class.                                   |
|    16                             |            super(LenetService, self).__init__(model_name, model_path)                         |
|    17                             |                                                                                               |
|    18                             |            # Configure preprocessing information.                                             |
|    19                             |            transformer = caffe.io.Transformer({'data': self.net.blobs['data'].data.shape})    |
|    20                             |            # Transform to NCHW.                                                               |
|    21                             |            transformer.set_transpose('data', (2, 0, 1))                                       |
|    22                             |            # Perform normalization.                                                           |
|    23                             |            transformer.set_raw_scale('data', 255.0)                                           |
|    24                             |                                                                                               |
|    25                             |            # If the batch size is set to 1, inference is supported for only one image.        |
|    26                             |            self.net.blobs['data'].reshape(1, 1, 28, 28)                                       |
|    27                             |            self.transformer = transformer                                                     |
|    28                             |                                                                                               |
|    29                             |           # Define the class labels.                                                          |
|    30                             |            self.label = [0,1,2,3,4,5,6,7,8,9]                                                 |
|    31                             |                                                                                               |
|    32                             |                                                                                               |
|    33                             |        def _preprocess(self, data):                                                           |
|    34                             |                                                                                               |
|    35                             |            for k, v in data.items():                                                          |
|    36                             |                for file_name, file_content in v.items():                                      |
|    37                             |                    im = caffe.io.load_image(file_content, color=False)                        |
|    38                             |                   # Pre-process the images.                                                   |
|    39                             |                    self.net.blobs['data'].data[...] = self.transformer.preprocess('data', im) |
|    40                             |                                                                                               |
|    41                             |                    return                                                                     |
|    42                             |                                                                                               |
|    43                             |        def _postprocess(self, data):                                                          |
|    44                             |                                                                                               |
|    45                             |            data = data['prob'][0, :]                                                          |
|    46                             |            predicted = np.argmax(data)                                                        |
|    47                             |            predicted = {"predicted" : str(predicted) }                                        |
|    48                             |                                                                                               |
|    49                             |            return predicted                                                                   |
+-----------------------------------+-----------------------------------------------------------------------------------------------+
