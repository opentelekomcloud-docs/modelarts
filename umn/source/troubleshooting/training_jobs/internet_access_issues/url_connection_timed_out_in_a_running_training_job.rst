:original_name: modelarts_13_0021.html

.. _modelarts_13_0021:

URL Connection Timed Out in a Running Training Job
==================================================

Symptom
-------

In a running training job, a URL connection timeout error occurs.

.. code-block::

   urllib.error.URLERROR:<urlopen error [Errno 110] Connection timed out>

Possible Causes
---------------

For security purposes, ModelArts is not allowed to access the Internet to download data.

Solution
--------

Download the required data to a local directory and upload it to OBS. Then, access the OBS path from ModelArts to obtain the data.
