:original_name: modelarts_05_0088.html

.. _modelarts_05_0088:

How Do I Install a Library That C++ Depends on?
===============================================

A third-party library may be used during job training. The following uses C++ as an example to describe how to install a third-party library.

#. Download source code to a local PC and upload it to OBS. For details about how to upload a file using OBS Browser, see .

#. Use MoXing to copy the source code uploaded to OBS to a notebook instance in the development environment.

   The following is a code example for copying data to a notebook instance in a development environment running on an EVS:

   .. code-block::

      import moxing as mox
      mox.file.make_dirs('/home/ma-user/work/data')
      mox.file.copy_parallel('obs://bucket-name/data', '/home/ma-user/work/data')

#. On the **Files** tab page of the **Jupyter** page, click **New** and select **Terminal**. Run the following command to go to the target path, and check whether the source code has been downloaded, that is, whether the **data** file exists.

   .. code-block::

      cd /home/ma-user/work
      ls

#. Compile code in **Terminal** based on service requirements.

#. Use MoXing to copy the compilation results to OBS. The following is a code example.

   .. code-block::

      import moxing as mox
      mox.file.make_dirs('/home/ma-user/work/data')
      mox.file.copy_parallel('/home/ma-user/work/data', 'obs://bucket-name/file)

#. During training, use MoXing to copy the compilation result from OBS to the container. The following is a code example.

   .. code-block::

      import moxing as mox
      mox.file.make_dirs('/cache/data')
      mox.file.copy_parallel('obs://bucket-name/data', '/cache/data')
