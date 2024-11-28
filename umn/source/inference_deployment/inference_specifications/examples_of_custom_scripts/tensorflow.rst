:original_name: inference-modelarts-0079.html

.. _inference-modelarts-0079:

TensorFlow
==========

There are two types of TensorFlow APIs, Keras and tf. They use different code for training and saving models, but the same code for inference.

Training a Model (Keras API)
----------------------------

::

   from keras.models import Sequential
   model = Sequential()
   from keras.layers import Dense
   import tensorflow as tf

   # Import a training dataset.
   mnist = tf.keras.datasets.mnist
   (x_train, y_train),(x_test, y_test) = mnist.load_data()
   x_train, x_test = x_train / 255.0, x_test / 255.0

   print(x_train.shape)

   from keras.layers import Dense
   from keras.models import Sequential
   import keras
   from keras.layers import Dense, Activation, Flatten, Dropout

   # Define a model network.
   model = Sequential()
   model.add(Flatten(input_shape=(28,28)))
   model.add(Dense(units=5120,activation='relu'))
   model.add(Dropout(0.2))

   model.add(Dense(units=10, activation='softmax'))

   # Define an optimizer and loss functions.
   model.compile(optimizer='adam',
                 loss='sparse_categorical_crossentropy',
                 metrics=['accuracy'])

   model.summary()
   # Train the model.
   model.fit(x_train, y_train, epochs=2)
   # Evaluate the model.
   model.evaluate(x_test, y_test)

Saving a Model (Keras API)
--------------------------

::

   from keras import backend as K

   # K.get_session().run(tf.global_variables_initializer())

   # Define the inputs and outputs of the prediction API.
   # The key values of the inputs and outputs dictionaries are used as the index keys for the input and output tensors of the model.
    # The input and output definitions of the model must match the custom inference script.
   predict_signature = tf.saved_model.signature_def_utils.predict_signature_def(
       inputs={"images" : model.input},
       outputs={"scores" : model.output}
   )

   # Define a save path.
   builder = tf.saved_model.builder.SavedModelBuilder('./mnist_keras/')

   builder.add_meta_graph_and_variables(

       sess = K.get_session(),
       # The tf.saved_model.tag_constants.SERVING tag needs to be defined for inference and deployment.
       tags=[tf.saved_model.tag_constants.SERVING],
       """
       signature_def_map: Only single items can exist, or the corresponding key needs to be defined as follows:
       tf.saved_model.signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY
       """
       signature_def_map={
           tf.saved_model.signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY:
               predict_signature
       }

   )
   builder.save()

Training a Model (tf API)
-------------------------

::

   from __future__ import print_function

   import gzip
   import os
   import urllib

   import numpy
   import tensorflow as tf
   from six.moves import urllib

   # Training data is obtained from the Yann LeCun official website http://yann.lecun.com/exdb/mnist/.
   SOURCE_URL = 'http://yann.lecun.com/exdb/mnist/'
   TRAIN_IMAGES = 'train-images-idx3-ubyte.gz'
   TRAIN_LABELS = 'train-labels-idx1-ubyte.gz'
   TEST_IMAGES = 't10k-images-idx3-ubyte.gz'
   TEST_LABELS = 't10k-labels-idx1-ubyte.gz'
   VALIDATION_SIZE = 5000


   def maybe_download(filename, work_directory):
       """Download the data from Yann's website, unless it's already here."""
       if not os.path.exists(work_directory):
           os.mkdir(work_directory)
       filepath = os.path.join(work_directory, filename)
       if not os.path.exists(filepath):
           filepath, _ = urllib.request.urlretrieve(SOURCE_URL + filename, filepath)
           statinfo = os.stat(filepath)
           print('Successfully downloaded %s %d bytes.' % (filename, statinfo.st_size))
       return filepath


   def _read32(bytestream):
       dt = numpy.dtype(numpy.uint32).newbyteorder('>')
       return numpy.frombuffer(bytestream.read(4), dtype=dt)[0]


   def extract_images(filename):
       """Extract the images into a 4D uint8 numpy array [index, y, x, depth]."""
       print('Extracting %s' % filename)
       with gzip.open(filename) as bytestream:
           magic = _read32(bytestream)
           if magic != 2051:
               raise ValueError(
                   'Invalid magic number %d in MNIST image file: %s' %
                   (magic, filename))
           num_images = _read32(bytestream)
           rows = _read32(bytestream)
           cols = _read32(bytestream)
           buf = bytestream.read(rows * cols * num_images)
           data = numpy.frombuffer(buf, dtype=numpy.uint8)
           data = data.reshape(num_images, rows, cols, 1)
           return data


   def dense_to_one_hot(labels_dense, num_classes=10):
       """Convert class labels from scalars to one-hot vectors."""
       num_labels = labels_dense.shape[0]
       index_offset = numpy.arange(num_labels) * num_classes
       labels_one_hot = numpy.zeros((num_labels, num_classes))
       labels_one_hot.flat[index_offset + labels_dense.ravel()] = 1
       return labels_one_hot


   def extract_labels(filename, one_hot=False):
       """Extract the labels into a 1D uint8 numpy array [index]."""
       print('Extracting %s' % filename)
       with gzip.open(filename) as bytestream:
           magic = _read32(bytestream)
           if magic != 2049:
               raise ValueError(
                   'Invalid magic number %d in MNIST label file: %s' %
                   (magic, filename))
           num_items = _read32(bytestream)
           buf = bytestream.read(num_items)
           labels = numpy.frombuffer(buf, dtype=numpy.uint8)
           if one_hot:
               return dense_to_one_hot(labels)
           return labels


   class DataSet(object):
       """Class encompassing test, validation and training MNIST data set."""

       def __init__(self, images, labels, fake_data=False, one_hot=False):
           """Construct a DataSet. one_hot arg is used only if fake_data is true."""

           if fake_data:
               self._num_examples = 10000
               self.one_hot = one_hot
           else:
               assert images.shape[0] == labels.shape[0], (
                       'images.shape: %s labels.shape: %s' % (images.shape,
                                                              labels.shape))
               self._num_examples = images.shape[0]

               # Convert shape from [num examples, rows, columns, depth]
               # to [num examples, rows*columns] (assuming depth == 1)
               assert images.shape[3] == 1
               images = images.reshape(images.shape[0],
                                       images.shape[1] * images.shape[2])
               # Convert from [0, 255] -> [0.0, 1.0].
               images = images.astype(numpy.float32)
               images = numpy.multiply(images, 1.0 / 255.0)
           self._images = images
           self._labels = labels
           self._epochs_completed = 0
           self._index_in_epoch = 0

       @property
       def images(self):
           return self._images

       @property
       def labels(self):
           return self._labels

       @property
       def num_examples(self):
           return self._num_examples

       @property
       def epochs_completed(self):
           return self._epochs_completed

       def next_batch(self, batch_size, fake_data=False):
           """Return the next `batch_size` examples from this data set."""
           if fake_data:
               fake_image = [1] * 784
               if self.one_hot:
                   fake_label = [1] + [0] * 9
               else:
                   fake_label = 0
               return [fake_image for _ in range(batch_size)], [
                   fake_label for _ in range(batch_size)
               ]
           start = self._index_in_epoch
           self._index_in_epoch += batch_size
           if self._index_in_epoch > self._num_examples:
               # Finished epoch
               self._epochs_completed += 1
               # Shuffle the data
               perm = numpy.arange(self._num_examples)
               numpy.random.shuffle(perm)
               self._images = self._images[perm]
               self._labels = self._labels[perm]
               # Start next epoch
               start = 0
               self._index_in_epoch = batch_size
               assert batch_size <= self._num_examples
           end = self._index_in_epoch
           return self._images[start:end], self._labels[start:end]


   def read_data_sets(train_dir, fake_data=False, one_hot=False):
       """Return training, validation and testing data sets."""

       class DataSets(object):
           pass

       data_sets = DataSets()

       if fake_data:
           data_sets.train = DataSet([], [], fake_data=True, one_hot=one_hot)
           data_sets.validation = DataSet([], [], fake_data=True, one_hot=one_hot)
           data_sets.test = DataSet([], [], fake_data=True, one_hot=one_hot)
           return data_sets

       local_file = maybe_download(TRAIN_IMAGES, train_dir)
       train_images = extract_images(local_file)

       local_file = maybe_download(TRAIN_LABELS, train_dir)
       train_labels = extract_labels(local_file, one_hot=one_hot)

       local_file = maybe_download(TEST_IMAGES, train_dir)
       test_images = extract_images(local_file)

       local_file = maybe_download(TEST_LABELS, train_dir)
       test_labels = extract_labels(local_file, one_hot=one_hot)

       validation_images = train_images[:VALIDATION_SIZE]
       validation_labels = train_labels[:VALIDATION_SIZE]
       train_images = train_images[VALIDATION_SIZE:]
       train_labels = train_labels[VALIDATION_SIZE:]

       data_sets.train = DataSet(train_images, train_labels)
       data_sets.validation = DataSet(validation_images, validation_labels)
       data_sets.test = DataSet(test_images, test_labels)
       return data_sets

   training_iteration = 1000

   modelarts_example_path =  './modelarts-mnist-train-save-deploy-example'

   export_path = modelarts_example_path + '/model/'
   data_path = './'

   print('Training model...')
   mnist = read_data_sets(data_path, one_hot=True)
   sess = tf.InteractiveSession()
   serialized_tf_example = tf.placeholder(tf.string, name='tf_example')
   feature_configs = {'x': tf.FixedLenFeature(shape=[784], dtype=tf.float32), }
   tf_example = tf.parse_example(serialized_tf_example, feature_configs)
   x = tf.identity(tf_example['x'], name='x')  # use tf.identity() to assign name
   y_ = tf.placeholder('float', shape=[None, 10])
   w = tf.Variable(tf.zeros([784, 10]))
   b = tf.Variable(tf.zeros([10]))
   sess.run(tf.global_variables_initializer())
   y = tf.nn.softmax(tf.matmul(x, w) + b, name='y')
   cross_entropy = -tf.reduce_sum(y_ * tf.log(y))
   train_step = tf.train.GradientDescentOptimizer(0.01).minimize(cross_entropy)
   values, indices = tf.nn.top_k(y, 10)
   table = tf.contrib.lookup.index_to_string_table_from_tensor(
       tf.constant([str(i) for i in range(10)]))
   prediction_classes = table.lookup(tf.to_int64(indices))
   for _ in range(training_iteration):
       batch = mnist.train.next_batch(50)
       train_step.run(feed_dict={x: batch[0], y_: batch[1]})
   correct_prediction = tf.equal(tf.argmax(y, 1), tf.argmax(y_, 1))
   accuracy = tf.reduce_mean(tf.cast(correct_prediction, 'float'))
   print('training accuracy %g' % sess.run(
       accuracy, feed_dict={
           x: mnist.test.images,
           y_: mnist.test.labels
       }))
   print('Done training!')

Saving a Model (tf API)
-----------------------

::

   # Export the model.
   # The model needs to be saved using the saved_model API.
   print('Exporting trained model to', export_path)
   builder = tf.saved_model.builder.SavedModelBuilder(export_path)

   tensor_info_x = tf.saved_model.utils.build_tensor_info(x)
   tensor_info_y = tf.saved_model.utils.build_tensor_info(y)

   # Define the inputs and outputs of the prediction API.
   # The key values of the inputs and outputs dictionaries are used as the index keys for the input and output tensors of the model.
    # The input and output definitions of the model must match the custom inference script.
   prediction_signature = (
       tf.saved_model.signature_def_utils.build_signature_def(
           inputs={'images': tensor_info_x},
           outputs={'scores': tensor_info_y},
           method_name=tf.saved_model.signature_constants.PREDICT_METHOD_NAME))

   legacy_init_op = tf.group(tf.tables_initializer(), name='legacy_init_op')
   builder.add_meta_graph_and_variables(
       # Set tag to serve/tf.saved_model.tag_constants.SERVING.
       sess, [tf.saved_model.tag_constants.SERVING],
       signature_def_map={
           'predict_images':
               prediction_signature,
       },
       legacy_init_op=legacy_init_op)

   builder.save()

   print('Done exporting!')

Inference Code (Keras and tf APIs)
----------------------------------

In the model inference code file **customize_service.py**, add a child model class which inherits properties from its parent model class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <en-us_topic_0000002079182509__en-us_topic_0172466150_table55021545175412>`.

::

   from PIL import Image
   import numpy as np
   from model_service.tfserving_model_service import TfServingBaseService


   class MnistService(TfServingBaseService):

       # Match the model input with the user's HTTPS API input during preprocessing.
       # The model input corresponding to the preceding training part is {"images":<array>}.
       def _preprocess(self, data):

           preprocessed_data = {}
           images = []
           # Iterate the input data.
           for k, v in data.items():
               for file_name, file_content in v.items():
                   image1 = Image.open(file_content)
                   image1 = np.array(image1, dtype=np.float32)
                   image1.resize((1,784))
                   images.append(image1)
           # Return the numpy array.
           images = np.array(images,dtype=np.float32)
           # Perform batch processing on multiple input samples and ensure that the shape is the same as that inputted during training.
           images.resize((len(data), 784))
           preprocessed_data['images'] = images
           return preprocessed_data

       # Processing logic of the inference for invoking the parent class.

       # The output corresponding to model saving in the preceding training part is {"scores":<array>}.
       # Postprocess the HTTPS output.
       def _postprocess(self, data):
           infer_output = {"mnist_result": []}
           # Iterate the model output.
           for output_name, results in data.items():
               for result in results:
                   infer_output["mnist_result"].append(result.index(max(result)))
           return infer_output
