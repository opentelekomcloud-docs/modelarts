:original_name: modelarts_05_0019.html

.. _modelarts_05_0019:

What Do I Do If the System Displays a Message Indicating that the AK/SK Pair Is Unavailable?
============================================================================================

Issue Analysis
--------------

An AK and SK form a key pair required for accessing OBS. Each SK corresponds to a specific AK, and each AK corresponds to a specific user. If the system displays a message indicating that the AK/SK pair is unavailable, it is possible that the account is in arrears or the AK/SK pair is incorrect.

Solution
--------

#. Use the current account to log in to the OBS console and check whether the current account can access OBS.

   -  If the account can access OBS, rectify the fault by referring to :ref:`2 <en-us_topic_0000002079104733__li181091239132313>`.

#. .. _en-us_topic_0000002079104733__li181091239132313:

   -  If yes, .
   -  If not, replace the AK/SK with those created using the current account. For details, see :ref:`Access Keys <modelarts_05_0004>`.
