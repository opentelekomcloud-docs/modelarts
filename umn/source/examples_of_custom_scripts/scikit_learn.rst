.. _modelarts_23_0179:

Scikit Learn
============

Training and Saving a Model
---------------------------

+-----------------------------------+----------------------------------------------------------------------+
| ::                                | ::                                                                   |
|                                   |                                                                      |
|     1                             |    import json                                                       |
|     2                             |    import pandas as pd                                               |
|     3                             |    from sklearn.datasets import load_iris                            |
|     4                             |    from sklearn.model_selection import train_test_split              |
|     5                             |    from sklearn.linear_model import LogisticRegression               |
|     6                             |    from sklearn.externals import joblib                              |
|     7                             |    iris = pd.read_csv('/data/iris.csv')                              |
|     8                             |    X = iris.drop(['virginica'],axis=1)                               |
|     9                             |    y = iris[['virginica']]                                           |
|    10                             |    # Create a LogisticRegression instance and train model            |
|    11                             |    logisticRegression = LogisticRegression(C=1000.0, random_state=0) |
|    12                             |    logisticRegression.fit(X,y)                                       |
|    13                             |    # Save model to local path                                        |
|    14                             |    joblib.dump(logisticRegression, '/tmp/sklearn.m')                 |
+-----------------------------------+----------------------------------------------------------------------+

After the model is saved, it must be uploaded to the OBS directory before being published. The **config.json** and **customize_service.py** files must be contained during publishing. For details about the definition method, see :ref:`Model Package Specifications <modelarts_23_0091>`.

Inference Code
--------------

+-----------------------------------+------------------------------------------------------------------------------------+
| ::                                | ::                                                                                 |
|                                   |                                                                                    |
|     1                             |    # coding:utf-8                                                                  |
|     2                             |    import collections                                                              |
|     3                             |    import json                                                                     |
|     4                             |    from sklearn.externals import joblib                                            |
|     5                             |    from model_service.python_model_service import XgSklServingBaseService          |
|     6                             |                                                                                    |
|     7                             |    class user_Service(XgSklServingBaseService):                                    |
|     8                             |                                                                                    |
|     9                             |        # request data preprocess                                                   |
|    10                             |        def _preprocess(self, data):                                                |
|    11                             |            list_data = []                                                          |
|    12                             |            json_data = json.loads(data, object_pairs_hook=collections.OrderedDict) |
|    13                             |            for element in json_data["data"]["req_data"]:                           |
|    14                             |                array = []                                                          |
|    15                             |                for each in element:                                                |
|    16                             |                    array.append(element[each])                                     |
|    17                             |                    list_data.append(array)                                         |
|    18                             |            return list_data                                                        |
|    19                             |                                                                                    |
|    20                             |        # predict                                                                   |
|    21                             |        def _inference(self, data):                                                 |
|    22                             |            sk_model = joblib.load(self.model_path)                                 |
|    23                             |            pre_result = sk_model.predict(data)                                     |
|    24                             |            pre_result = pre_result.tolist()                                        |
|    25                             |            return pre_result                                                       |
|    26                             |                                                                                    |
|    27                             |        # predict result process                                                    |
|    28                             |        def _postprocess(self,data):                                                |
|    29                             |            resp_data = []                                                          |
|    30                             |            for element in data:                                                    |
|    31                             |                resp_data.append({"predictresult": element})                        |
|    32                             |            return resp_data                                                        |
+-----------------------------------+------------------------------------------------------------------------------------+
