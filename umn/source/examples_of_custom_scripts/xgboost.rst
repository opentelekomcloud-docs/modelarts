:original_name: modelarts_23_0177.html

.. _modelarts_23_0177:

XGBoost
=======

Training and Saving a Model
---------------------------

::

   import pandas as pd
   import xgboost as xgb
   from sklearn.model_selection import train_test_split

   # Prepare training data and setting parameters
   iris = pd.read_csv('/home/ma-user/work/iris.csv')
   X = iris.drop(['variety'],axis=1)
   y = iris[['variety']]
   X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1234565)
   params = {
       'booster': 'gbtree',
       'objective': 'multi:softmax',
       'num_class': 3,
       'gamma': 0.1,
       'max_depth': 6,
       'lambda': 2,
       'subsample': 0.7,
       'colsample_bytree': 0.7,
       'min_child_weight': 3,
       'silent': 1,
       'eta': 0.1,
       'seed': 1000,
       'nthread': 4,
   }
   plst = params.items()
   dtrain = xgb.DMatrix(X_train, y_train)
   num_rounds = 500
   model = xgb.train(plst, dtrain, num_rounds)
   model.save_model('/tmp/xgboost.m')

Before training, download the **iris.csv** dataset, decompress it, and upload it to the **/home/ma-user/work/** directory of the notebook instance. Download the **iris.csv** dataset from https://gist.github.com/netj/8836201. For details about how to upload a file to a notebook instance, see .

After the model is saved, it must be uploaded to the OBS directory before being published. The **config.json** configuration and the **customize_service.py** inference code must be included during the publishing. For details about how to compile **config.json**, see :ref:`Specifications for Compiling the Model Configuration File <modelarts_23_0092>`. For details about inference code, see :ref:`Inference Code <modelarts_23_0177__en-us_topic_0196941733_section6122193511917>`.

.. _modelarts_23_0177__en-us_topic_0196941733_section6122193511917:

Inference Code
--------------

Inference code must be inherited from the BaseService class. For details about the import statements of different types of parent model classes, see :ref:`Table 1 <modelarts_23_0093__en-us_topic_0172466150_table55021545175412>`.

.. code-block::

   # coding:utf-8
   import collections
   import json
   import xgboost as xgb
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

       #   predict
       def _inference(self, data):
           xg_model = xgb.Booster(model_file=self.model_path)
           pre_data = xgb.DMatrix(data)
           pre_result = xg_model.predict(pre_data)
           pre_result = pre_result.tolist()
           return pre_result

       # predict result process
       def _postprocess(self,data):
           resp_data = []
           for element in data:
               resp_data.append({"predictresult": element})
           return resp_data
