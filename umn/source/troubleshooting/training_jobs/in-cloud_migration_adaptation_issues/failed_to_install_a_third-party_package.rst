:original_name: modelarts_13_0015.html

.. _modelarts_13_0015:

Failed to Install a Third-Party Package
=======================================

Symptom
-------

-  :ref:`How to install custom library functions <en-us_topic_0000001943967785__li054160134317>` for ModelArts, for example, **apex**.

-  The following error occurs when a third-party package is installed in the ModelArts training environment:

   .. code-block::

      xxx.whl is not a supported wheel on this platform

Possible Cause
--------------

Error **xxx.whl is not a supported wheel on this platform** occurs, because the format of the name of the installed file is not supported. For details about the solution, see :ref:`2 <en-us_topic_0000001943967785__li21626333431>`.

Solution
--------

#. .. _en-us_topic_0000001943967785__li054160134317:

   **Installing the third-party package**

   a. For an existing package in **pip**, run the following code to install it:

      .. code-block::

         import os
         os.system('pip install xxx')

   b. For a package that do not exist in **pip**, for example, **apex**, use the following method to upload the installation package to an OBS bucket. In this example, the installation package has been uploaded to **obs://cnnorth4-test/codes/mox_benchmarks/apex-master/**. Add the following code to the boot file to install the package:

      .. code-block::

         try:
             import apex
         except Exception:
             import os
             import moxing as mox
             mox.file.copy_parallel('obs://cnnorth4-test/codes/mox_benchmarks/apex-master/', '/cache/apex-master')
             os.system('pip --default-timeout=100 install -v --no-cache-dir --global-option="--cpp_ext" --global-option="--cuda_ext" /cache/apex-master')

#. .. _en-us_topic_0000001943967785__li21626333431:

   **Installation error**

   If the **xxx.whl** file fails to be installed, perform the following steps to solve the problem:

   a. If the **xxx.whl** file fails to be installed, add the following code to the boot file to check the file name and version supported by the **pip** command.

      .. code-block::

         import pip
         print(pip.pep425tags.get_supported())

      The supported file names and versions are as follows:

      .. code-block::

         [('cp36', 'cp36m', 'manylinux1_x86_64'), ('cp36', 'cp36m', 'linux_x86_64'), ('cp36', 'abi3', 'manylinux1_x86_64'), ('cp36', 'abi3', 'linux_x86_64'), ('cp36', 'none', 'manylinux1_x86_64'), ('cp36', 'none', 'linux_x86_64'), ('cp35', 'abi3', 'manylinux1_x86_64'), ('cp35', 'abi3', 'linux_x86_64'), ('cp34', 'abi3', 'manylinux1_x86_64'), ('cp34', 'abi3', 'linux_x86_64'), ('cp33', 'abi3', 'manylinux1_x86_64'), ('cp33', 'abi3', 'linux_x86_64'), ('cp32', 'abi3', 'manylinux1_x86_64'), ('cp32', 'abi3', 'linux_x86_64'), ('py3', 'none', 'manylinux1_x86_64'), ('py3', 'none', 'linux_x86_64'), ('cp36', 'none', 'any'), ('cp3', 'none', 'any'), ('py36', 'none', 'any'), ('py3', 'none', 'any'), ('py35', 'none', 'any'), ('py34', 'none', 'any'), ('py33', 'none', 'any'), ('py32', 'none', 'any'), ('py31', 'none', 'any'), ('py30', 'none', 'any')]

   b. Change **faiss_gpu-1.5.3-cp36-cp36m-manylinux2010_x86_64.whl** to **faiss_gpu-1.5.3-cp36-cp36m-manylinux1_x86_64.whl**, and run the following code to install the package:

      .. code-block::

         import moxing as mox
         import os

         mox.file.copy('obs://wolfros-net/zp/AI/code/faiss_gpu-1.5.3-cp36-cp36m-manylinux2010_x86_64.whl','/cache/faiss_gpu-1.5.3-cp36-cp36m-manylinux1_x86_64.whl')
         os.system('pip install /cache/faiss_gpu-1.5.3-cp36-cp36m-manylinux1_x86_64.whl')
