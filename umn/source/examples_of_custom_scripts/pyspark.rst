.. _modelarts_23_0178:

PySpark
=======

Training and Saving a Model
---------------------------

+-----------------------------------+------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                       |
|                                   |                                                                                          |
|     1                             |    from pyspark.ml import Pipeline, PipelineModel                                        |
|     2                             |    from pyspark.ml.linalg import Vectors                                                 |
|     3                             |    from pyspark.ml.classification import LogisticRegression                              |
|     4                             |                                                                                          |
|     5                             |    # Prepare training data using tuples.                                                 |
|     6                             |    # Prepare training data from a list of (label, features) tuples.                      |
|     7                             |    training = spark.createDataFrame([                                                    |
|     8                             |        (1.0, Vectors.dense([0.0, 1.1, 0.1])),                                            |
|     9                             |        (0.0, Vectors.dense([2.0, 1.0, -1.0])),                                           |
|    10                             |        (0.0, Vectors.dense([2.0, 1.3, 1.0])),                                            |
|    11                             |        (1.0, Vectors.dense([0.0, 1.2, -0.5]))], ["label", "features"])                   |
|    12                             |                                                                                          |
|    13                             |    # Create a training instance. The logistic regression algorithm is used for training. |
|    14                             |    # Create a LogisticRegression instance. This instance is an Estimator.                |
|    15                             |    lr = LogisticRegression(maxIter=10, regParam=0.01)                                    |
|    16                             |                                                                                          |
|    17                             |    # Train the logistic regression model.                                                |
|    18                             |    # Learn a LogisticRegression model. This uses the parameters stored in lr.            |
|    19                             |    model = lr.fit(training)                                                              |
|    20                             |                                                                                          |
|    21                             |    # Save the model to a local directory.                                                |
|    22                             |    # Save model to local path.                                                           |
|    23                             |    model.save("/tmp/spark_model")                                                        |
+-----------------------------------+------------------------------------------------------------------------------------------+

After the model is saved, it must be uploaded to the OBS directory before being published. The **config.json** configuration and **customize_service.py** must be contained during publishing. For details about the definition method, see :ref:`Model Package Specifications <modelarts_23_0091>`.

Inference Code
--------------

+-----------------------------------+------------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                   |
|                                   |                                                                                                      |
|     1                             |    # coding:utf-8                                                                                    |
|     2                             |    import collections                                                                                |
|     3                             |    import json                                                                                       |
|     4                             |    import traceback                                                                                  |
|     5                             |                                                                                                      |
|     6                             |    import model_service.log as log                                                                   |
|     7                             |    from model_service.spark_model_service import SparkServingBaseService                             |
|     8                             |    from pyspark.ml.classification import LogisticRegression                                          |
|     9                             |                                                                                                      |
|    10                             |    logger = log.getLogger(__name__)                                                                  |
|    11                             |                                                                                                      |
|    12                             |                                                                                                      |
|    13                             |    class user_Service(SparkServingBaseService):                                                      |
|    14                             |        # Pre-process data.                                                                           |
|    15                             |        def _preprocess(self, data):                                                                  |
|    16                             |            logger.info("Begin to handle data from user data...")                                     |
|    17                             |            # Read data.                                                                              |
|    18                             |            req_json = json.loads(data, object_pairs_hook=collections.OrderedDict)                    |
|    19                             |            try:                                                                                      |
|    20                             |                # Convert data to the spark dataframe format.                                         |
|    21                             |                predict_spdf = self.spark.createDataFrame(pd.DataFrame(req_json["data"]["req_data"])) |
|    22                             |            except Exception as e:                                                                    |
|    23                             |                logger.error("check your request data does meet the requirements ?")                  |
|    24                             |                logger.error(traceback.format_exc())                                                  |
|    25                             |                raise Exception("check your request data does meet the requirements ?")               |
|    26                             |            return predict_spdf                                                                       |
|    27                             |                                                                                                      |
|    28                             |        # Perform model inference.                                                                    |
|    29                             |        def _inference(self, data):                                                                   |
|    30                             |            try:                                                                                      |
|    31                             |                 # Load a model file.                                                                 |
|    32                             |                predict_model = LogisticRegression.load(self.model_path)                              |
|    33                             |                # Perform data inference.                                                             |
|    34                             |                prediction_result = predict_model.transform(data)                                     |
|    35                             |        except Exception as e:                                                                        |
|    36                             |                logger.error(traceback.format_exc())                                                  |
|    37                             |                raise Exception("Unable to load model and do dataframe transformation.")              |
|    38                             |            return prediction_result                                                                  |
|    39                             |                                                                                                      |
|    40                             |        # Post-process data.                                                                          |
|    41                             |        def _postprocess(self, pre_data):                                                             |
|    42                             |            logger.info("Get new data to respond...")                                                 |
|    43                             |            predict_str = pre_data.toPandas().to_json(orient='records')                               |
|    44                             |            predict_result = json.loads(predict_str)                                                  |
|    45                             |            return predict_result                                                                     |
+-----------------------------------+------------------------------------------------------------------------------------------------------+
