.. _modelarts_23_0177:

XGBoost
=======

Training and Saving a Model
---------------------------

+-----------------------------------+---------------------------------------------------------------------------------------------------+
| ::                                | ::                                                                                                |
|                                   |                                                                                                   |
|     1                             |    import pandas as pd                                                                            |
|     2                             |    import xgboost as xgb                                                                          |
|     3                             |    from sklearn.model_selection import train_test_split                                           |
|     4                             |                                                                                                   |
|     5                             |    # Prepare training data and setting parameters                                                 |
|     6                             |    iris = pd.read_csv('/data/iris.csv')                                                           |
|     7                             |    X = iris.drop(['virginica'],axis=1)                                                            |
|     8                             |    y = iris[['virginica']]                                                                        |
|     9                             |    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=1234565) |
|    10                             |    params = {                                                                                     |
|    11                             |        'booster': 'gbtree',                                                                       |
|    12                             |        'objective': 'multi:softmax',                                                              |
|    13                             |        'num_class': 3,                                                                            |
|    14                             |        'gamma': 0.1,                                                                              |
|    15                             |        'max_depth': 6,                                                                            |
|    16                             |        'lambda': 2,                                                                               |
|    17                             |        'subsample': 0.7,                                                                          |
|    18                             |        'colsample_bytree': 0.7,                                                                   |
|    19                             |        'min_child_weight': 3,                                                                     |
|    20                             |        'silent': 1,                                                                               |
|    21                             |        'eta': 0.1,                                                                                |
|    22                             |        'seed': 1000,                                                                              |
|    23                             |        'nthread': 4,                                                                              |
|    24                             |    }                                                                                              |
|    25                             |    plst = params.items()                                                                          |
|    26                             |    dtrain = xgb.DMatrix(X_train, y_train)                                                         |
|    27                             |    num_rounds = 500                                                                               |
|    28                             |    model = xgb.train(plst, dtrain, num_rounds)                                                    |
|    29                             |    model.save_model('/tmp/xgboost.m')                                                             |
+-----------------------------------+---------------------------------------------------------------------------------------------------+

After the model is saved, it must be uploaded to the OBS directory before being published. The **config.json** and **customize_service.py** files must be contained during publishing. For details about the definition method, see :ref:`Model Package Specifications <modelarts_23_0091>`.

Inference Code
--------------

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
