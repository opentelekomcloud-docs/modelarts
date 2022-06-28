:original_name: modelarts_23_0179.html

.. _modelarts_23_0179:

Scikit Learn
============

Training and Saving a Model
---------------------------

.. code-block::

   import json
   import pandas as pd
   from sklearn.datasets import load_iris
   from sklearn.model_selection import train_test_split
   from sklearn.linear_model import LogisticRegression
   from sklearn.externals import joblib
   iris = pd.read_csv('/home/ma-user/work/iris.csv')
   X = iris.drop(['variety'],axis=1)
   y = iris[['variety']]
   # Create a LogisticRegression instance and train model
   logisticRegression = LogisticRegression(C=1000.0, random_state=0)
   logisticRegression.fit(X,y)
   # Save model to local path
   joblib.dump(logisticRegression, '/tmp/sklearn.m')

Before training, download the **iris.csv** dataset, decompress it, and upload it to the **/home/ma-user/work/** directory of the notebook instance. Download the **iris.csv** dataset from https://gist.github.com/netj/8836201.

After the model is saved, it must be uploaded to the OBS directory before being published. The **config.json** and **customize_service.py** files must be contained during publishing. For details about the definition method, see :ref:`Model Package Specifications <modelarts_23_0091>`.

Inference Code
--------------

.. code-block::

   # coding:utf-8
   import collections
   import json
   from sklearn.externals import joblib
   from model_service.python_model_service import XgSklServingBaseService

   class user_Service(XgSklServingBaseService):

       # request data preprocess
       def _preprocess(self, data):
           list_data = []
           json_data = json.loads(data, object_pairs_hook=collections.OrderedDict)
           for element in json_data["data"]["req_data"]:
               array = []
               for each in element:
                   array.append(element[each])
                   list_data.append(array)
           return list_data

       # predict
       def _inference(self, data):
           sk_model = joblib.load(self.model_path)
           pre_result = sk_model.predict(data)
           pre_result = pre_result.tolist()
           return pre_result

       # predict result process
       def _postprocess(self,data):
           resp_data = []
           for element in data:
               resp_data.append({"predictresult": element})
           return resp_data
