:original_name: modelarts_13_0026.html

.. _modelarts_13_0026:

Creating a KVStore Using MXNet Blocked and No Error Reported
============================================================

Symptom
-------

When **kv_store = mxnet.kv.create('dist_async')** is used to create **kvstore**, the program is blocked. For example, run the following code. If **end** is not displayed, the program is blocked.

.. code-block::

   print('start')
   kv_store = mxnet.kv.create('dist_async')
   print('end')

Possible Cause
--------------

The possible cause of a worker block is that the server cannot be connected.

Solution
--------

Place the following code before **import mxnet** in **Boot File** to check the communication status between nodes. In addition, ps can be resent.

.. code-block::

   import os
   os.environ['PS_VERBOSE'] = '2'
   os.environ['PS_RESEND'] = '1'

In the preceding code, **os.environ['PS_VERBOSE'] = '2'** indicates that all communication information is printed. **os.environ['PS_RESEND'] = '1'** indicates that the Van instance resends the message if it does not receive the ACK message within the milliseconds set by **PS_RESEND_TIMEOUT**.
