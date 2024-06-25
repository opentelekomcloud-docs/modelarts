:original_name: modelarts_13_0042.html

.. _modelarts_13_0042:

ModelArts.6333 Error Occurs
===========================

Symptom
-------

When you use a notebook instance, the ModelArts.6333 error is displayed.

Possible Cause
--------------

The fault may be caused by instance overload. The notebook instance automatically restores. Refresh the page and wait for several minutes. The common cause is that the memory is used up.

Solution
--------

When this error occurs, the notebook instance automatically restores. You can refresh the page and wait for several minutes.

The common cause is that the memory is used up. You can use the following methods to rectify the fault.

-  Method 1: Replace the notebook instance with a resource with higher specifications.
-  Method 2: Adjust the parameters in the code to reduce memory occupation. If the memory is still insufficient after the code is modified, use method 1.

   #. Call the sklearn method **silhouette_score(addr_1,siteskmeans.labels)** and specify the **sample_size** parameter to reduce memory occupation.
   #. When calling the **train** method, you can try to decrease the value of **batch_size**.
