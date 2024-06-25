:original_name: modelarts_trouble_0053.html

.. _modelarts_trouble_0053:

Error Message "Out of bounds nanosecond timestamp" Displayed in Logs
====================================================================

Symptom
-------

When pandas.to_datetime is used to convert time, the following error message is displayed:

.. code-block::

   pandas._libs.tslibs.np_datetime.OutOfBoundsDatetime: Out of bounds nanosecond timestamp: 1-01-02 13:20:00

Possible Causes
---------------

The time is out of the permitted range. For details, see the `official document <https://pandas.pydata.org/docs/dev/user_guide/timeseries.html#timestamp-limitations>`__.

Solution
--------

Check the time. Timestamps in pandas are in the unit of nanosecond. Ensure that the time is within the following permitted range:

-  Earliest time: 1677-09-22 00:12:43.145225
-  Latest time: 2262-04-11 23:47:16.854775807

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
