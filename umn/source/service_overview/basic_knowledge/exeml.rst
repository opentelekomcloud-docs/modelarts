:original_name: modelarts_01_0016.html

.. _modelarts_01_0016:

ExeML
=====

To implement AI in various industries, AI model development must be simplified. Currently, only a few algorithm engineers and researchers are capable of AI development and optimization. They find it challenging to develop related prototypes into products and projects. Most service developers, however, face difficulties in developing AI algorithms and optimizing parameters. As a result, most enterprises lack comprehensive AI development capabilities.

ModelArts uses machine learning to help service developers who are not experienced in algorithm development to develop algorithms. It automatically generates models based on transfer learning and Neural Architecture Search (NAS), selects parameters for model training, and performs model optimization. This helps service developers quickly complete model training and deployment. Based on the labeled data and application scenario provided by developers, ModelArts automatically generates models that meet precision requirements, without the need for coding. The application scenarios include image classification, object detection, and predictive analytics. Models can be automatically optimized and generated based on the deployment environment and inference speed requirements.


.. figure:: /_static/images/en-us_image_0000002079098833.png
   :alt: **Figure 1** Process of using ExeML

   **Figure 1** Process of using ExeML

ModelArts ExeML also provides the auto learning white-box capabilities. It opens model parameters and implements template-based development. ExeML helps accelerate the development speed. With ExeML, developers can directly optimize the generated model or retrain the model, instead of setting up a new model.

The key techniques of ExeML are tree search-based optimal feature transformation and Bayesian optimization for automatic parameter adjustment based on the maximum information entropy model. With these key technologies, data features and patterns can be automatically learned from enterprise relational (structured) data, and machine learning models and parameters can be intelligently optimized, achieving the same level accuracy that is achieved by experts. The key technologies of auto deep learning are transfer learning (high-quality models are generated based on a small amount of data), auto design of the model architecture in multiple dimensions (neural network search and adaptive model optimization), and auto optimization and training of training parameters.
