:original_name: modelarts_04_0198.html

.. _modelarts_04_0198:

Deleting a Model
================

You can use the API to delete a model object.

Sample Code
-----------

In a ModelArts notebook instance, you do not need to enter authentication parameters for session authentication. For details about session authentication of other development environments, see :ref:`Session Authentication <modelarts_04_0123>`.

-  Method 1: Delete the model created in :ref:`Importing a Model <modelarts_04_0194>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_instance = Model(session, model_id="input your model_id")
      model_instance.delete_model()

-  Method 2: Delete the model object returned in :ref:`Obtaining the Model Object List <modelarts_04_0196>`.

   ::

      from modelarts.session import Session
      from modelarts.model import Model
      session = Session()
      model_object_list = Model.get_model_object_list(session)
      model_instance = model_object_list[0]
      model_instance.delete_model()
