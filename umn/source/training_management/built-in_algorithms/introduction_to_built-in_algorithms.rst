:original_name: modelarts_23_0045.html

.. _modelarts_23_0045:

Introduction to Built-in Algorithms
===================================

Based on the frequently-used AI engines in the industry, ModelArts provides built-in algorithms to meet a wide range of your requirements. You can directly select the algorithms for training jobs, without concerning model development.

Built-in algorithms of ModelArts adopt MXNet and TensorFlow engines and are mainly used for detection of object classes and locations, image classification, and semantic image segmentation.

Viewing Built-in Algorithms
---------------------------

In the left navigation pane of the ModelArts management console, choose **Training Management** > **Training Jobs**. On the displayed page, click **Built-in Algorithms**. In the built-in algorithm list, click |image1| next to an algorithm name to view details about the algorithm.

You can click **Create Training Job** in the **Operation** column for an algorithm to quickly create a training job, for which this algorithm serves as the **Algorithm Source**.

.. note::

   Before using a built-in algorithm to create a training job, prepare and upload training data to OBS. For details about the data storage path and data format requirements, see :ref:`Requirements on Datasets <modelarts_23_0157>`.

For details about the built-in algorithms and their running parameters, see the following:

-  :ref:`yolo_v3 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section927534914236>`
-  :ref:`retinanet_resnet_v1_50 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section14756183063012>`
-  :ref:`inception_v3 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section8882739173020>`
-  :ref:`darknet_53 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section1371034453015>`
-  :ref:`SegNet_VGG_BN_16 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section1411685323014>`
-  :ref:`ResNet_v2_50 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section1422116595303>`
-  :ref:`ResNet_v1_50 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section175188416313>`
-  :ref:`Faster_RCNN_ResNet_v2_101 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section184719918316>`
-  :ref:`Faster_RCNN_ResNet_v1_50 <modelarts_23_0158__en-us_topic_0259701754_en-us_topic_0189694045_section1794118221311>`

.. |image1| image:: /_static/images/en-us_image_0000001455265565.gif
