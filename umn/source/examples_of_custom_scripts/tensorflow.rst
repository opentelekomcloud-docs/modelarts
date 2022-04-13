.. _modelarts_23_0173:

TensorFlow
==========

TensorFlow has two types of APIs: Keras and tf. Keras and tf use different code for training and saving models, but the same code for inference.

Training a Model (Keras API)
----------------------------

+-----------------------------------+-----------------------------------------------------------------+
| ::                                | ::                                                              |
|                                   |                                                                 |
|     1                             |    from keras.models import Sequential                          |
|     2                             |    model = Sequential()                                         |
|     3                             |    from keras.layers import Dense                               |
|     4                             |    import tensorflow as tf                                      |
|     5                             |                                                                 |
|     6                             |    # Import a training dataset.                                 |
|     7                             |    mnist = tf.keras.datasets.mnist                              |
|     8                             |    (x_train, y_train),(x_test, y_test) = mnist.load_data()      |
|     9                             |    x_train, x_test = x_train / 255.0, x_test / 255.0            |
|    10                             |                                                                 |
|    11                             |    print(x_train.shape)                                         |
|    12                             |                                                                 |
|    13                             |    from keras.layers import Dense                               |
|    14                             |    from keras.models import Sequential                          |
|    15                             |    import keras                                                 |
|    16                             |    from keras.layers import Dense, Activation, Flatten, Dropout |
|    17                             |                                                                 |
|    18                             |    # Define a model network.                                    |
|    19                             |    model = Sequential()                                         |
|    20                             |    model.add(Flatten(input_shape=(28,28)))                      |
|    21                             |    model.add(Dense(units=5120,activation='relu'))               |
|    22                             |    model.add(Dropout(0.2))                                      |
|    23                             |                                                                 |
|    24                             |    model.add(Dense(units=10, activation='softmax'))             |
|    25                             |                                                                 |
|    26                             |    # Define an optimizer and loss functions.                    |
|    27                             |    model.compile(optimizer='adam',                              |
|    28                             |                  loss='sparse_categorical_crossentropy',        |
|    29                             |                  metrics=['accuracy'])                          |
|    30                             |                                                                 |
|    31                             |    model.summary()                                              |
|    32                             |    # Train the model.                                           |
|    33                             |    model.fit(x_train, y_train, epochs=2)                        |
|    34                             |    # Evaluate the model.                                        |
|    35                             |    model.evaluate(x_test, y_test)                               |
+-----------------------------------+-----------------------------------------------------------------+

Saving a Model (Keras API)
--------------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                                                   |
|                                   |                                                                                                                                      |
|     1                             |    from keras import backend as K                                                                                                    |
|     2                             |                                                                                                                                      |
|     3                             |    # K.get_session().run(tf.global_variables_initializer())                                                                          |
|     4                             |                                                                                                                                      |
|     5                             |    # Define the inputs and outputs of the prediction API.                                                                            |
|     6                             |    # The key values of the inputs and outputs dictionaries are used as the index keys for the input and output tensors of the model. |
|     7                             |     # The input and output definitions of the model must match the custom inference script.                                          |
|     8                             |    predict_signature = tf.saved_model.signature_def_utils.predict_signature_def(                                                     |
|     9                             |        inputs={"images" : model.input},                                                                                              |
|    10                             |        outputs={"scores" : model.output}                                                                                             |
|    11                             |    )                                                                                                                                 |
|    12                             |                                                                                                                                      |
|    13                             |    # Define a save path.                                                                                                             |
|    14                             |    builder = tf.saved_model.builder.SavedModelBuilder('./mnist_keras/')                                                              |
|    15                             |                                                                                                                                      |
|    16                             |    builder.add_meta_graph_and_variables(                                                                                             |
|    17                             |                                                                                                                                      |
|    18                             |        sess = K.get_session(),                                                                                                       |
|    19                             |        # The tf.saved_model.tag_constants.SERVING tag needs to be defined for inference and deployment.                              |
|    20                             |        tags=[tf.saved_model.tag_constants.SERVING],                                                                                  |
|    21                             |        """                                                                                                                           |
|    22                             |        signature_def_map: Only single items can exist, or the corresponding key needs to be defined as follows:                      |
|    23                             |        tf.saved_model.signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY                                                          |
|    24                             |        """                                                                                                                           |
|    25                             |        signature_def_map={                                                                                                           |
|    26                             |            tf.saved_model.signature_constants.DEFAULT_SERVING_SIGNATURE_DEF_KEY:                                                     |
|    27                             |                predict_signature                                                                                                     |
|    28                             |        }                                                                                                                             |
|    29                             |                                                                                                                                      |
|    30                             |    )                                                                                                                                 |
|    31                             |    builder.save()                                                                                                                    |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+

Training a Model (tf API)
-------------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                     |
|                                   |                                                                                                        |
|      1                            |    from __future__ import print_function                                                               |
|      2                            |                                                                                                        |
|      3                            |    import gzip                                                                                         |
|      4                            |    import os                                                                                           |
|      5                            |    import urllib                                                                                       |
|      6                            |                                                                                                        |
|      7                            |    import numpy                                                                                        |
|      8                            |    import tensorflow as tf                                                                             |
|      9                            |    from six.moves import urllib                                                                        |
|     10                            |                                                                                                        |
|     11                            |    # Training data is obtained from the Yann LeCun official website http://yann.lecun.com/exdb/mnist/. |
|     12                            |    SOURCE_URL = 'http://yann.lecun.com/exdb/mnist/'                                                    |
|     13                            |    TRAIN_IMAGES = 'train-images-idx3-ubyte.gz'                                                         |
|     14                            |    TRAIN_LABELS = 'train-labels-idx1-ubyte.gz'                                                         |
|     15                            |    TEST_IMAGES = 't10k-images-idx3-ubyte.gz'                                                           |
|     16                            |    TEST_LABELS = 't10k-labels-idx1-ubyte.gz'                                                           |
|     17                            |    VALIDATION_SIZE = 5000                                                                              |
|     18                            |                                                                                                        |
|     19                            |                                                                                                        |
|     20                            |    def maybe_download(filename, work_directory):                                                       |
|     21                            |        """Download the data from Yann's website, unless it's already here."""                          |
|     22                            |        if not os.path.exists(work_directory):                                                          |
|     23                            |            os.mkdir(work_directory)                                                                    |
|     24                            |        filepath = os.path.join(work_directory, filename)                                               |
|     25                            |        if not os.path.exists(filepath):                                                                |
|     26                            |            filepath, _ = urllib.request.urlretrieve(SOURCE_URL + filename, filepath)                   |
|     27                            |            statinfo = os.stat(filepath)                                                                |
|     28                            |            print('Successfully downloaded %s %d bytes.' % (filename, statinfo.st_size))                |
|     29                            |        return filepath                                                                                 |
|     30                            |                                                                                                        |
|     31                            |                                                                                                        |
|     32                            |    def _read32(bytestream):                                                                            |
|     33                            |        dt = numpy.dtype(numpy.uint32).newbyteorder('>')                                                |
|     34                            |        return numpy.frombuffer(bytestream.read(4), dtype=dt)[0]                                        |
|     35                            |                                                                                                        |
|     36                            |                                                                                                        |
|     37                            |    def extract_images(filename):                                                                       |
|     38                            |        """Extract the images into a 4D uint8 numpy array [index, y, x, depth]."""                      |
|     39                            |        print('Extracting %s' % filename)                                                               |
|     40                            |        with gzip.open(filename) as bytestream:                                                         |
|     41                            |            magic = _read32(bytestream)                                                                 |
|     42                            |            if magic != 2051:                                                                           |
|     43                            |                raise ValueError(                                                                       |
|     44                            |                    'Invalid magic number %d in MNIST image file: %s' %                                 |
|     45                            |                    (magic, filename))                                                                  |
|     46                            |            num_images = _read32(bytestream)                                                            |
|     47                            |            rows = _read32(bytestream)                                                                  |
|     48                            |            cols = _read32(bytestream)                                                                  |
|     49                            |            buf = bytestream.read(rows * cols * num_images)                                             |
|     50                            |            data = numpy.frombuffer(buf, dtype=numpy.uint8)                                             |
|     51                            |            data = data.reshape(num_images, rows, cols, 1)                                              |
|     52                            |            return data                                                                                 |
|     53                            |                                                                                                        |
|     54                            |                                                                                                        |
|     55                            |    def dense_to_one_hot(labels_dense, num_classes=10):                                                 |
|     56                            |        """Convert class labels from scalars to one-hot vectors."""                                     |
|     57                            |        num_labels = labels_dense.shape[0]                                                              |
|     58                            |        index_offset = numpy.arange(num_labels) * num_classes                                           |
|     59                            |        labels_one_hot = numpy.zeros((num_labels, num_classes))                                         |
|     60                            |        labels_one_hot.flat[index_offset + labels_dense.ravel()] = 1                                    |
|     61                            |        return labels_one_hot                                                                           |
|     62                            |                                                                                                        |
|     63                            |                                                                                                        |
|     64                            |    def extract_labels(filename, one_hot=False):                                                        |
|     65                            |        """Extract the labels into a 1D uint8 numpy array [index]."""                                   |
|     66                            |        print('Extracting %s' % filename)                                                               |
|     67                            |        with gzip.open(filename) as bytestream:                                                         |
|     68                            |            magic = _read32(bytestream)                                                                 |
|     69                            |            if magic != 2049:                                                                           |
|     70                            |                raise ValueError(                                                                       |
|     71                            |                    'Invalid magic number %d in MNIST label file: %s' %                                 |
|     72                            |                    (magic, filename))                                                                  |
|     73                            |            num_items = _read32(bytestream)                                                             |
|     74                            |            buf = bytestream.read(num_items)                                                            |
|     75                            |            labels = numpy.frombuffer(buf, dtype=numpy.uint8)                                           |
|     76                            |            if one_hot:                                                                                 |
|     77                            |                return dense_to_one_hot(labels)                                                         |
|     78                            |            return labels                                                                               |
|     79                            |                                                                                                        |
|     80                            |                                                                                                        |
|     81                            |    class DataSet(object):                                                                              |
|     82                            |        """Class encompassing test, validation and training MNIST data set."""                          |
|     83                            |                                                                                                        |
|     84                            |        def __init__(self, images, labels, fake_data=False, one_hot=False):                             |
|     85                            |            """Construct a DataSet. one_hot arg is used only if fake_data is true."""                   |
|     86                            |                                                                                                        |
|     87                            |            if fake_data:                                                                               |
|     88                            |                self._num_examples = 10000                                                              |
|     89                            |                self.one_hot = one_hot                                                                  |
|     90                            |            else:                                                                                       |
|     91                            |                assert images.shape[0] == labels.shape[0], (                                            |
|     92                            |                        'images.shape: %s labels.shape: %s' % (images.shape,                            |
|     93                            |                                                               labels.shape))                           |
|     94                            |                self._num_examples = images.shape[0]                                                    |
|     95                            |                                                                                                        |
|     96                            |                # Convert shape from [num examples, rows, columns, depth]                               |
|     97                            |                # to [num examples, rows*columns] (assuming depth == 1)                                 |
|     98                            |                assert images.shape[3] == 1                                                             |
|     99                            |                images = images.reshape(images.shape[0],                                                |
|    100                            |                                        images.shape[1] * images.shape[2])                              |
|    101                            |                # Convert from [0, 255] -> [0.0, 1.0].                                                  |
|    102                            |                images = images.astype(numpy.float32)                                                   |
|    103                            |                images = numpy.multiply(images, 1.0 / 255.0)                                            |
|    104                            |            self._images = images                                                                       |
|    105                            |            self._labels = labels                                                                       |
|    106                            |            self._epochs_completed = 0                                                                  |
|    107                            |            self._index_in_epoch = 0                                                                    |
|    108                            |                                                                                                        |
|    109                            |        @property                                                                                       |
|    110                            |        def images(self):                                                                               |
|    111                            |            return self._images                                                                         |
|    112                            |                                                                                                        |
|    113                            |        @property                                                                                       |
|    114                            |        def labels(self):                                                                               |
|    115                            |            return self._labels                                                                         |
|    116                            |                                                                                                        |
|    117                            |        @property                                                                                       |
|    118                            |        def num_examples(self):                                                                         |
|    119                            |            return self._num_examples                                                                   |
|    120                            |                                                                                                        |
|    121                            |        @property                                                                                       |
|    122                            |        def epochs_completed(self):                                                                     |
|    123                            |            return self._epochs_completed                                                               |
|    124                            |                                                                                                        |
|    125                            |        def next_batch(self, batch_size, fake_data=False):                                              |
|    126                            |            """Return the next `batch_size` examples from this data set."""                             |
|    127                            |            if fake_data:                                                                               |
|    128                            |                fake_image = [1] * 784                                                                  |
|    129                            |                if self.one_hot:                                                                        |
|    130                            |                    fake_label = [1] + [0] * 9                                                          |
|    131                            |                else:                                                                                   |
|    132                            |                    fake_label = 0                                                                      |
|    133                            |                return [fake_image for _ in range(batch_size)], [                                       |
|    134                            |                    fake_label for _ in range(batch_size)                                               |
|    135                            |                ]                                                                                       |
|    136                            |            start = self._index_in_epoch                                                                |
|    137                            |            self._index_in_epoch += batch_size                                                          |
|    138                            |            if self._index_in_epoch > self._num_examples:                                               |
|    139                            |                # Finished epoch                                                                        |
|    140                            |                self._epochs_completed += 1                                                             |
|    141                            |                # Shuffle the data                                                                      |
|    142                            |                perm = numpy.arange(self._num_examples)                                                 |
|    143                            |                numpy.random.shuffle(perm)                                                              |
|    144                            |                self._images = self._images[perm]                                                       |
|    145                            |                self._labels = self._labels[perm]                                                       |
|    146                            |                # Start next epoch                                                                      |
|    147                            |                start = 0                                                                               |
|    148                            |                self._index_in_epoch = batch_size                                                       |
|    149                            |                assert batch_size <= self._num_examples                                                 |
|    150                            |            end = self._index_in_epoch                                                                  |
|    151                            |            return self._images[start:end], self._labels[start:end]                                     |
|    152                            |                                                                                                        |
|    153                            |                                                                                                        |
|    154                            |    def read_data_sets(train_dir, fake_data=False, one_hot=False):                                      |
|    155                            |        """Return training, validation and testing data sets."""                                        |
|    156                            |                                                                                                        |
|    157                            |        class DataSets(object):                                                                         |
|    158                            |            pass                                                                                        |
|    159                            |                                                                                                        |
|    160                            |        data_sets = DataSets()                                                                          |
|    161                            |                                                                                                        |
|    162                            |        if fake_data:                                                                                   |
|    163                            |            data_sets.train = DataSet([], [], fake_data=True, one_hot=one_hot)                          |
|    164                            |            data_sets.validation = DataSet([], [], fake_data=True, one_hot=one_hot)                     |
|    165                            |            data_sets.test = DataSet([], [], fake_data=True, one_hot=one_hot)                           |
|    166                            |            return data_sets                                                                            |
|    167                            |                                                                                                        |
|    168                            |        local_file = maybe_download(TRAIN_IMAGES, train_dir)                                            |
|    169                            |        train_images = extract_images(local_file)                                                       |
|    170                            |                                                                                                        |
|    171                            |        local_file = maybe_download(TRAIN_LABELS, train_dir)                                            |
|    172                            |        train_labels = extract_labels(local_file, one_hot=one_hot)                                      |
|    173                            |                                                                                                        |
|    174                            |        local_file = maybe_download(TEST_IMAGES, train_dir)                                             |
|    175                            |        test_images = extract_images(local_file)                                                        |
|    176                            |                                                                                                        |
|    177                            |        local_file = maybe_download(TEST_LABELS, train_dir)                                             |
|    178                            |        test_labels = extract_labels(local_file, one_hot=one_hot)                                       |
|    179                            |                                                                                                        |
|    180                            |        validation_images = train_images[:VALIDATION_SIZE]                                              |
|    181                            |        validation_labels = train_labels[:VALIDATION_SIZE]                                              |
|    182                            |        train_images = train_images[VALIDATION_SIZE:]                                                   |
|    183                            |        train_labels = train_labels[VALIDATION_SIZE:]                                                   |
|    184                            |                                                                                                        |
|    185                            |        data_sets.train = DataSet(train_images, train_labels)                                           |
|    186                            |        data_sets.validation = DataSet(validation_images, validation_labels)                            |
|    187                            |        data_sets.test = DataSet(test_images, test_labels)                                              |
|    188                            |        return data_sets                                                                                |
|    189                            |                                                                                                        |
|    190                            |    training_iteration = 1000                                                                           |
|    191                            |                                                                                                        |
|    192                            |    modelarts_example_path =  './modelarts-mnist-train-save-deploy-example'                             |
|    193                            |                                                                                                        |
|    194                            |    export_path = modelarts_example_path + '/model/'                                                    |
|    195                            |    data_path = './'                                                                                    |
|    196                            |                                                                                                        |
|    197                            |    print('Training model...')                                                                          |
|    198                            |    mnist = read_data_sets(data_path, one_hot=True)                                                     |
|    199                            |    sess = tf.InteractiveSession()                                                                      |
|    200                            |    serialized_tf_example = tf.placeholder(tf.string, name='tf_example')                                |
|    201                            |    feature_configs = {'x': tf.FixedLenFeature(shape=[784], dtype=tf.float32), }                        |
|    202                            |    tf_example = tf.parse_example(serialized_tf_example, feature_configs)                               |
|    203                            |    x = tf.identity(tf_example['x'], name='x')  # use tf.identity() to assign name                      |
|    204                            |    y_ = tf.placeholder('float', shape=[None, 10])                                                      |
|    205                            |    w = tf.Variable(tf.zeros([784, 10]))                                                                |
|    206                            |    b = tf.Variable(tf.zeros([10]))                                                                     |
|    207                            |    sess.run(tf.global_variables_initializer())                                                         |
|    208                            |    y = tf.nn.softmax(tf.matmul(x, w) + b, name='y')                                                    |
|    209                            |    cross_entropy = -tf.reduce_sum(y_ * tf.log(y))                                                      |
|    210                            |    train_step = tf.train.GradientDescentOptimizer(0.01).minimize(cross_entropy)                        |
|    211                            |    values, indices = tf.nn.top_k(y, 10)                                                                |
|    212                            |    table = tf.contrib.lookup.index_to_string_table_from_tensor(                                        |
|    213                            |        tf.constant([str(i) for i in range(10)]))                                                       |
|    214                            |    prediction_classes = table.lookup(tf.to_int64(indices))                                             |
|    215                            |    for _ in range(training_iteration):                                                                 |
|    216                            |        batch = mnist.train.next_batch(50)                                                              |
|    217                            |        train_step.run(feed_dict={x: batch[0], y_: batch[1]})                                           |
|    218                            |    correct_prediction = tf.equal(tf.argmax(y, 1), tf.argmax(y_, 1))                                    |
|    219                            |    accuracy = tf.reduce_mean(tf.cast(correct_prediction, 'float'))                                     |
|    220                            |    print('training accuracy %g' % sess.run(                                                            |
|    221                            |        accuracy, feed_dict={                                                                           |
|    222                            |            x: mnist.test.images,                                                                       |
|    223                            |            y_: mnist.test.labels                                                                       |
|    224                            |        }))                                                                                             |
|    225                            |    print('Done training!')                                                                             |
+-----------------------------------+--------------------------------------------------------------------------------------------------------+

Saving a Model (tf API)
-----------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                                                   |
|                                   |                                                                                                                                      |
|     1                             |    # Export the model.                                                                                                               |
|     2                             |    # The model needs to be saved using the saved_model API.                                                                          |
|     3                             |    print('Exporting trained model to', export_path)                                                                                  |
|     4                             |    builder = tf.saved_model.builder.SavedModelBuilder(export_path)                                                                   |
|     5                             |                                                                                                                                      |
|     6                             |    tensor_info_x = tf.saved_model.utils.build_tensor_info(x)                                                                         |
|     7                             |    tensor_info_y = tf.saved_model.utils.build_tensor_info(y)                                                                         |
|     8                             |                                                                                                                                      |
|     9                             |    # Define the inputs and outputs of the prediction API.                                                                            |
|    10                             |    # The key values of the inputs and outputs dictionaries are used as the index keys for the input and output tensors of the model. |
|    11                             |     # The input and output definitions of the model must match the custom inference script.                                          |
|    12                             |    prediction_signature = (                                                                                                          |
|    13                             |        tf.saved_model.signature_def_utils.build_signature_def(                                                                       |
|    14                             |            inputs={'images': tensor_info_x},                                                                                         |
|    15                             |            outputs={'scores': tensor_info_y},                                                                                        |
|    16                             |            method_name=tf.saved_model.signature_constants.PREDICT_METHOD_NAME))                                                      |
|    17                             |                                                                                                                                      |
|    18                             |    legacy_init_op = tf.group(tf.tables_initializer(), name='legacy_init_op')                                                         |
|    19                             |    builder.add_meta_graph_and_variables(                                                                                             |
|    20                             |        # Set tag to serve/tf.saved_model.tag_constants.SERVING.                                                                      |
|    21                             |        sess, [tf.saved_model.tag_constants.SERVING],                                                                                 |
|    22                             |        signature_def_map={                                                                                                           |
|    23                             |            'predict_images':                                                                                                         |
|    24                             |                prediction_signature,                                                                                                 |
|    25                             |        },                                                                                                                            |
|    26                             |        legacy_init_op=legacy_init_op)                                                                                                |
|    27                             |                                                                                                                                      |
|    28                             |    builder.save()                                                                                                                    |
|    29                             |                                                                                                                                      |
|    30                             |    print('Done exporting!')                                                                                                          |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+

Inference Code (Keras and tf APIs)
----------------------------------

+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                                                      |
|                                   |                                                                                                                                         |
|     1                             |    from PIL import Image                                                                                                                |
|     2                             |    import numpy as np                                                                                                                   |
|     3                             |    from model_service.tfserving_model_service import TfServingBaseService                                                               |
|     4                             |                                                                                                                                         |
|     5                             |                                                                                                                                         |
|     6                             |    class mnist_service(TfServingBaseService):                                                                                           |
|     7                             |                                                                                                                                         |
|     8                             |        # Match the model input with the user's HTTPS API input during preprocessing.                                                    |
|     9                             |        # The model input corresponding to the preceding training part is {"images":<array>}.                                            |
|    10                             |        def _preprocess(self, data):                                                                                                     |
|    11                             |                                                                                                                                         |
|    12                             |            preprocessed_data = {}                                                                                                       |
|    13                             |            images = []                                                                                                                  |
|    14                             |            # Iterate the input data.                                                                                                    |
|    15                             |            for k, v in data.items():                                                                                                    |
|    16                             |                for file_name, file_content in v.items():                                                                                |
|    17                             |                    image1 = Image.open(file_content)                                                                                    |
|    18                             |                    image1 = np.array(image1, dtype=np.float32)                                                                          |
|    19                             |                    image1.resize((1,784))                                                                                               |
|    20                             |                    images.append(image1)                                                                                                |
|    21                             |            # Return the numpy array.                                                                                                    |
|    22                             |            images = np.array(images,dtype=np.float32)                                                                                   |
|    23                             |            # Perform batch processing on multiple input samples and ensure that the shape is the same as that inputted during training. |
|    24                             |            images.resize((len(data), 784))                                                                                              |
|    25                             |            preprocessed_data['images'] = images                                                                                         |
|    26                             |            return preprocessed_data                                                                                                     |
|    27                             |                                                                                                                                         |
|    28                             |        # Processing logic of the inference for invoking the parent class.                                                               |
|    29                             |                                                                                                                                         |
|    30                             |        # The output corresponding to model saving in the preceding training part is {"scores":<array>}.                                 |
|    31                             |        # Postprocess the HTTPS output.                                                                                                  |
|    32                             |        def _postprocess(self, data):                                                                                                    |
|    33                             |            infer_output = {"mnist_result": []}                                                                                          |
|    34                             |            # Iterate the model output.                                                                                                  |
|    35                             |            for output_name, results in data.items():                                                                                    |
|    36                             |                for result in results:                                                                                                   |
|    37                             |                    infer_output["mnist_result"].append(result.index(max(result)))                                                       |
|    38                             |            return infer_output                                                                                                          |
+-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
