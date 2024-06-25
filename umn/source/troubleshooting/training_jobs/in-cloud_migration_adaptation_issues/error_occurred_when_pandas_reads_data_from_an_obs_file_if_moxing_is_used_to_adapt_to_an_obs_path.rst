:original_name: modelarts_trouble_0033.html

.. _modelarts_trouble_0033:

Error Occurred When Pandas Reads Data from an OBS File If MoXing Is Used to Adapt to an OBS Path
================================================================================================

Symptom
-------

If MoXing is used to adapt to an OBS path, an error occurs when pandas of a later version reads data from an OBS file.

.. code-block::

   1. 'can't decode byte xxx in position xxx'
   2. 'OSError:File isn't open for writing'

Possible Causes
---------------

MoXing does not support Pandas of a later version.

Solution
--------

#. After the OBS path is adapted, change the file access mode from **r** to **rb** and change the **\_write_check_passed** value in **mox.file.File** to **True**, as shown in the following is sample code:

   .. code-block::

      import pandas as pd
      import moxing as mox

      mox.file.shift('os', 'mox')  # Replace the open operation of the operating system with the operation for adapting the mox.file.File to the OBS path.

      param = {'encoding': 'utf-8'}
      path = 'xxx.csv'
      with open(path, 'rb') as f:
          f._wirte_check_passed = True
          df = pd.read_csv(ff, **param)

#. Use the local PyCharm to remotely access notebook for debugging.

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
