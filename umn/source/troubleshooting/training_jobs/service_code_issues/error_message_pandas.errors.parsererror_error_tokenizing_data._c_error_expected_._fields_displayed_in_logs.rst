:original_name: modelarts_trouble_0050.html

.. _modelarts_trouble_0050:

Error Message "pandas.errors.ParserError: Error tokenizing data. C error: Expected .\* fields" Displayed in Logs
================================================================================================================

Symptom
-------

When pandas is used to read CSV data, the following error is displayed in logs, and the training job failed:

.. code-block::

   pandas.errors.ParserError: Error tokenizing data. C error: Expected 4 field

Possible Causes
---------------

The number of columns in each row of the CSV file is different.

Solution
--------

Use either of the following methods to resolve this issue:

-  Check the CSV file and delete the lines with extra columns.

-  Run the following commands to ignore the lines with extra columns:

   .. code-block::

      import pandas as pd
      pd.read_csv(filePath,error_bad_lines=False)

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
