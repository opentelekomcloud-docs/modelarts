:original_name: modelarts_21_0077.html

.. _modelarts_21_0077:

What Should I Know When Setting Training Parameters?
====================================================

Pay attention to the following when setting training parameters:

-  When setting running parameters for creating a training job, you only need to set the corresponding parameter names and values. See :ref:`Figure 1 <modelarts_21_0077__en-us_topic_0198838770_fig1638314610491>`.

   .. _modelarts_21_0077__en-us_topic_0198838770_fig1638314610491:

   .. figure:: /_static/images/en-us_image_0000001455265985.png
      :alt: **Figure 1** Setting running parameters

      **Figure 1** Setting running parameters

-  If a parameter value is an OBS bucket path, use the path to the data. See :ref:`Figure 2 <modelarts_21_0077__en-us_topic_0198838770_fig392681318596>`.

   .. _modelarts_21_0077__en-us_topic_0198838770_fig392681318596:

   .. figure:: /_static/images/en-us_image_0000001404986122.png
      :alt: **Figure 2** Configuring an OBS path

      **Figure 2** Configuring an OBS path

-  When creating an OBS folder in code, you need to call a MoXing API as follows:

   .. code-block::

      import moxing as mox
      mox.file.make_dirs('obs://bucket_name/sub_dir_0/sub_dir_1')
