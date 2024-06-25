:original_name: modelarts_05_0374.html

.. _modelarts_05_0374:

How Can I Obtain GPU Usage Through Code?
========================================

Run the shell or python command to obtain the GPU usage.

Using the shell Command
-----------------------

#. Run the **nvidia-smi** command.

   This operation relies on CUDA NVCC.

   .. code-block::

      watch -n 1 nvidia-smi

   |image1|

#. Run the **gpustat** command.

   .. code-block::

      pip install gpustat

   .. code-block::

      gpustat -cp -i

   |image2|

   To stop the command execution, press **Ctrl+C**.

Using the python Command
------------------------

#. Run the **nvidia-ml-py3** command (commonly used).

   .. code-block::

      !pip install nvidia-ml-py3

   .. code-block::

      import nvidia_smi
      nvidia_smi.nvmlInit()
      deviceCount = nvidia_smi.nvmlDeviceGetCount()
      for i in range(deviceCount):
          handle = nvidia_smi.nvmlDeviceGetHandleByIndex(i)
          util = nvidia_smi.nvmlDeviceGetUtilizationRates(handle)
          mem = nvidia_smi.nvmlDeviceGetMemoryInfo(handle)
          print(f"|Device {i}| Mem Free: {mem.free/1024**2:5.2f}MB / {mem.total/1024**2:5.2f}MB | gpu-util: {util.gpu:3.1%} | gpu-mem: {util.memory:3.1%} |")

   |image3|

#. Run the **nvidia_smi**, **wapper**, and **prettytable** commands.

   Use the decorator to obtain the GPU usage in real time during model training.

   .. code-block::

      def gputil_decorator(func):
          def wrapper(*args, **kwargs):
              import nvidia_smi
              import prettytable as pt

              try:
                  table = pt.PrettyTable(['Devices','Mem Free','GPU-util','GPU-mem'])
                  nvidia_smi.nvmlInit()
                  deviceCount = nvidia_smi.nvmlDeviceGetCount()
                  for i in range(deviceCount):
                      handle = nvidia_smi.nvmlDeviceGetHandleByIndex(i)
                      res = nvidia_smi.nvmlDeviceGetUtilizationRates(handle)
                      mem = nvidia_smi.nvmlDeviceGetMemoryInfo(handle)
                      table.add_row([i, f"{mem.free/1024**2:5.2f}MB/{mem.total/1024**2:5.2f}MB", f"{res.gpu:3.1%}", f"{res.memory:3.1%}"])

              except nvidia_smi.NVMLError as error:
                  print(error)

              print(table)
              return func(*args, **kwargs)
          return wrapper

   |image4|

#. Run the **pynvml** command.

   Run **nvidia-ml-py3** to directly obtain the nvml c-lib library, without using **nvidia-smi**. Therefore, this command is recommended.

   .. code-block::

      from pynvml import *
      nvmlInit()
      handle = nvmlDeviceGetHandleByIndex(0)
      info = nvmlDeviceGetMemoryInfo(handle)
      print("Total memory:", info.total)
      print("Free memory:", info.free)
      print("Used memory:", info.used)

   |image5|

#. Run the **gputil** command.

   .. code-block::

      !pip install gputil

   .. code-block::

      import GPUtil as GPU
      GPU.showUtilization()

   |image6|

   .. code-block::

      import GPUtil as GPU
      GPUs = GPU.getGPUs()
      for gpu in GPUs:
          print("GPU RAM Free: {0:.0f}MB | Used: {1:.0f}MB | Util {2:3.0f}% | Total {3:.0f}MB".format(gpu.memoryFree, gpu.memoryUsed, gpu.memoryUtil*100, gpu.memoryTotal))

   |image7|

   **When using a deep learning framework such as PyTorch or TensorFlow, you can also use the APIs provided by the framework for query.**

.. |image1| image:: /_static/images/en-us_image_0000001910018974.png
.. |image2| image:: /_static/images/en-us_image_0000001910058990.png
.. |image3| image:: /_static/images/en-us_image_0000001943978149.png
.. |image4| image:: /_static/images/en-us_image_0000001943978153.png
.. |image5| image:: /_static/images/en-us_image_0000001943978157.png
.. |image6| image:: /_static/images/en-us_image_0000001910018966.png
.. |image7| image:: /_static/images/en-us_image_0000001910018978.png
