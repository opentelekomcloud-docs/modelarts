:original_name: modelarts_trouble_0063.html

.. _modelarts_trouble_0063:

Error Message "AttributeError: 'NoneType' object has no attribute 'dtype'" Displayed in Logs
============================================================================================

Symptom
-------

Code can run properly in the notebook Keras image. When tensorflow.keras is used for training, error message "AttributeError: 'NoneType' object has no attribute 'dtype'" is displayed.

Possible Causes
---------------

The NumPy version of the training image is different from that in the notebook instance.

Solution
--------

Print the NumPy version in the code and check whether the version is 1.18.5. If the version is not 1.18.5, run the following command at the beginning of the code:

.. code-block::

   import os
   os.system('pip install numpy==1.18.5')

If the error persists, modify the preceding code as follows:

.. code-block::

   import os
   os.system('pip install numpy==1.18.5')
   os.system('pip install keras==2.6.0')
   os.system('pip install tensorflow==2.6.0')
