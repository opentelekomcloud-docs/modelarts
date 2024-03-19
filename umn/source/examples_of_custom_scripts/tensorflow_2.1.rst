:original_name: modelarts_23_0301.html

.. _modelarts_23_0301:

TensorFlow 2.1
==============

Training and Saving a Model
---------------------------

.. code-block::

   from __future__ import absolute_import, division, print_function, unicode_literals

   import tensorflow as tf

   mnist = tf.keras.datasets.mnist

   (x_train, y_train), (x_test, y_test) = mnist.load_data()
   x_train, x_test = x_train / 255.0, x_test / 255.0

   model = tf.keras.models.Sequential([
       tf.keras.layers.Flatten(input_shape=(28, 28)),
       tf.keras.layers.Dense(128, activation='relu'),
       tf.keras.layers.Dense(256, activation='relu'),
       tf.keras.layers.Dropout(0.2),
       # Name the output layer output, which is used to obtain the result during model inference.
       tf.keras.layers.Dense(10, activation='softmax', name="output")
   ])

   model.compile(optimizer='adam',
                 loss='sparse_categorical_crossentropy',
                 metrics=['accuracy'])

   model.fit(x_train, y_train, epochs=10)

   tf.keras.models.save_model(model, "./mnist")

Inference Code
--------------

Inference code must be inherited from the BaseService class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <modelarts_23_0093__en-us_topic_0172466150_table55021545175412>`.

.. code-block::

   import logging
   import threading

   import numpy as np
   import tensorflow as tf
   from PIL import Image

   from model_service.tfserving_model_service import TfServingBaseService

   logger = logging.getLogger()
   logger.setLevel(logging.INFO)


   class mnist_service(TfServingBaseService):

       def __init__(self, model_name, model_path):
           self.model_name = model_name
           self.model_path = model_path
           self.model = None
           self.predict = None

          # The label file can be loaded here and used in the post-processing function.
           # Directories for storing the label.txt file on OBS and in the model package

           # with open(os.path.join(self.model_path, 'label.txt')) as f:
           #     self.label = json.load(f)
           # Load the model in saved_model format in non-blocking mode to prevent blocking timeout.
           thread = threading.Thread(target=self.load_model)
           thread.start()

       def load_model(self):
           # Load the model in saved_model format.
           self.model = tf.saved_model.load(self.model_path)

           signature_defs = self.model.signatures.keys()

           signature = []
           # only one signature allowed
           for signature_def in signature_defs:
               signature.append(signature_def)

           if len(signature) == 1:
               model_signature = signature[0]
           else:
               logging.warning("signatures more than one, use serving_default signature from %s", signature)
               model_signature = tf.saved_model.DEFAULT_SERVING_SIGNATURE_DEF_KEY

           self.predict = self.model.signatures[model_signature]

       def _preprocess(self, data):
           images = []
           for k, v in data.items():
               for file_name, file_content in v.items():
                   image1 = Image.open(file_content)
                   image1 = np.array(image1, dtype=np.float32)
                   image1.resize((28, 28, 1))
                   images.append(image1)

           images = tf.convert_to_tensor(images, dtype=tf.dtypes.float32)
           preprocessed_data = images

           return preprocessed_data

       def _inference(self, data):

           return self.predict(data)

       def _postprocess(self, data):

           return {
               "result": int(data["output"].numpy()[0].argmax())
           }
