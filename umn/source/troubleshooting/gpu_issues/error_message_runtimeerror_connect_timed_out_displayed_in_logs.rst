:original_name: modelarts_trouble_0043.html

.. _modelarts_trouble_0043:

Error Message "RuntimeError: connect() timed out" Displayed in Logs
===================================================================

Symptom
-------

When PyTorch was used for distributed training, the following error occurred.


.. figure:: /_static/images/en-us_image_0000001799338988.png
   :alt: **Figure 1** Error log

   **Figure 1** Error log

Possible Causes
---------------

The possible causes are as follows:

If data had been copied before this issue occurred, data replication of all nodes was not completed at the same time. If you executed **torch.distributed.init_process_group()** when data replication was still in progress on certain nodes, the execution timed out.

Solution
--------

If the issue is caused by asynchronous data copy between nodes and no barrier occurs, execute **torch.distributed.init_process_group()** before copying data, copy data based on **local_rank()==0**, call **torch.distributed.barrier()**, and wait until data copy is complete on all nodes. For details, see the following code:

.. code-block::

   import moxing as mox
   import torch

   torch.distributed.init_process_group()
   if local_rank == 0:
       mox.file.copy_parallel(src,dst)

   torch.distributed.barrier()

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
