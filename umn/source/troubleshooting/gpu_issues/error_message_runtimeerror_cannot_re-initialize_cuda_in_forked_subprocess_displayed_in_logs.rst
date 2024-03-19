:original_name: modelarts_trouble_0051.html

.. _modelarts_trouble_0051:

Error Message "RuntimeError: Cannot re-initialize CUDA in forked subprocess" Displayed in Logs
==============================================================================================

Symptom
-------

When PyTorch was used to start multiple processes, the following error message was displayed:

.. code-block::

   RuntimeError: Cannot re-initialize CUDA in forked subprocess

Possible Causes
---------------

The possible causes are as follows:

The boot mode of multi-processing is incorrect.

Solution
--------

Resolve the issue by referring to `Writing Distributed Applications with PyTorch <https://pytorch.org/tutorials/intermediate/dist_tuto.html#setup>`__.

.. code-block::

   """run.py:"""
   #!/usr/bin/env python
   import os
   import torch
   import torch.distributed as dist
   import torch.multiprocessing as mp

   def run(rank, size):
       """ Distributed function to be implemented later. """
       pass

   def init_process(rank, size, fn, backend='gloo'):
       """ Initialize the distributed environment. """
       os.environ['MASTER_ADDR'] = '127.0.0.1'
       os.environ['MASTER_PORT'] = '29500'
       dist.init_process_group(backend, rank=rank, world_size=size)
       fn(rank, size)


   if __name__ == "__main__":
       size = 2
       processes = []
       mp.set_start_method("spawn")
       for rank in range(size):
           p = mp.Process(target=init_process, args=(rank, size, run))
           p.start()
           processes.append(p)

       for p in processes:
           p.join()

Summary and Suggestions
-----------------------

Before creating a training job, use the ModelArts development environment to debug the training code to maximally eliminate errors in code migration.
