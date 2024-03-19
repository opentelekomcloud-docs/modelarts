:original_name: modelarts_23_0178.html

.. _modelarts_23_0178:

Spark
=====

Training and Saving a Model
---------------------------

::

   from pyspark.ml import Pipeline, PipelineModel
   from pyspark.ml.linalg import Vectors
   from pyspark.ml.classification import LogisticRegression

   # Prepare training data using tuples.
   # Prepare training data from a list of (label, features) tuples.
   training = spark.createDataFrame([
       (1.0, Vectors.dense([0.0, 1.1, 0.1])),
       (0.0, Vectors.dense([2.0, 1.0, -1.0])),
       (0.0, Vectors.dense([2.0, 1.3, 1.0])),
       (1.0, Vectors.dense([0.0, 1.2, -0.5]))], ["label", "features"])

   # Create a training instance. The logistic regression algorithm is used for training.
   # Create a LogisticRegression instance. This instance is an Estimator.
   lr = LogisticRegression(maxIter=10, regParam=0.01)

   # Train the logistic regression model.
   # Learn a LogisticRegression model. This uses the parameters stored in lr.
   model = lr.fit(training)

   # Save the model to a local directory.
   # Save model to local path.
   model.save("/tmp/spark_model")

After the model is saved, it must be uploaded to the OBS directory before being published. The **config.json** configuration and the **customize_service.py** inference code must be included during the publishing. For details about how to compile **config.json**, see :ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`. For details about inference code, see :ref:`Inference Code <modelarts_23_0178__en-us_topic_0196941734_section6122193511917>`.

.. _modelarts_23_0178__en-us_topic_0196941734_section6122193511917:

Inference Code
--------------

Inference code must be inherited from the BaseService class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <modelarts_23_0093__en-us_topic_0172466150_table55021545175412>`.

::

   # coding:utf-8
   import collections
   import json
   import traceback

   import model_service.log as log
   from model_service.spark_model_service import SparkServingBaseService
   from pyspark.ml.classification import LogisticRegression

   logger = log.getLogger(__name__)


   class user_Service(SparkServingBaseService):
       # Pre-process data.
       def _preprocess(self, data):
           logger.info("Begin to handle data from user data...")
           # Read data.
           req_json = json.loads(data, object_pairs_hook=collections.OrderedDict)
           try:
               # Convert data to the spark dataframe format.
               predict_spdf = self.spark.createDataFrame(pd.DataFrame(req_json["data"]["req_data"]))
           except Exception as e:
               logger.error("check your request data does meet the requirements ?")
               logger.error(traceback.format_exc())
               raise Exception("check your request data does meet the requirements ?")
           return predict_spdf

       # Perform model inference.
       def _inference(self, data):
           try:
                # Load a model file.
               predict_model = LogisticRegression.load(self.model_path)
               # Perform data inference.
               prediction_result = predict_model.transform(data)
       except Exception as e:
               logger.error(traceback.format_exc())
               raise Exception("Unable to load model and do dataframe transformation.")
           return prediction_result

       # Post-process data.
       def _postprocess(self, pre_data):
           logger.info("Get new data to respond...")
           predict_str = pre_data.toPandas().to_json(orient='records')
           predict_result = json.loads(predict_str)
           return predict_result
