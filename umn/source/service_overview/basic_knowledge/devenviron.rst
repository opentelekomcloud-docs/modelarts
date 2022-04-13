.. _modelarts_01_0013:

DevEnviron
==========

It is challenging to set up a development environment, select an AI algorithm framework and algorithm, debug code, install software, and accelerate hardware. To address these challenges, ModelArts provides DevEnviron to simplify the entire development process.

-  **Mainstream AI algorithm frameworks supported**

   In the machine learning and deep learning fields, popular open-source training and inference frameworks include TensorFlow, PyTorch, MXNet, and MindSpore. ModelArts supports all popular AI computing frameworks and provides a user-friendly development and debugging environment. It supports traditional machine learning algorithms, such as logistic regression, decision tree, and clustering, as well as multiple types of deep learning algorithms, such as the convolutional neural network (CNN), recurrent neural network (RNN), and long short-term memory (LSTM).

-  **Simplified algorithm development for distributed training**

   Deep learning generally requires large-scale GPU clusters for distributed acceleration. For existing open-source frameworks, algorithm developers need to write a large amount of code for distributed training on different hardware, and the acceleration code varies depending on the framework. To resolve these issues, a distributed lightweight framework or SDK is required. The framework or SDK is built on deep learning engines such as TensorFlow, PyTorch, MXNet, and MindSpore to improve the distributed performance and usability of these engines. ModelArts MoXing perfectly suits the needs. The easy-to-use MoXing API/SDK enables you to develop deep learning at low costs.
