:original_name: modelarts_13_0113.html

.. _modelarts_13_0113:

What Do I Do If a Notebook Instance Won't Run My Code?
======================================================

If a notebook instance fails to execute code, you can locate and rectify the fault as follows:

#. If the execution of a cell is suspended or lasts for a long time (for example, the execution of the second and third cells in :ref:`Figure 1 <en-us_topic_0000002233739436__en-us_topic_0183089532_fig54529362315>` is suspended or lasts for a long time, causing execution failure of the fourth cell) but the notebook page still responds and other cells can be selected, click **interrupt the kernel** highlighted in a red box in the following figure to stop the execution of all cells. The notebook instance retains all variable spaces.

   .. _en-us_topic_0000002233739436__en-us_topic_0183089532_fig54529362315:

   .. figure:: /_static/images/en-us_image_0000002268739217.png
      :alt: **Figure 1** Stopping all cells

      **Figure 1** Stopping all cells

#. If the notebook page does not respond, close the notebook page and the ModelArts console. Then, open the ModelArts console and access the notebook instance again. The notebook instance retains all the variable spaces that exist when the notebook instance is unavailable.

#. If the notebook instance still cannot be used, access the **Notebook** page on the ModelArts console and stop the notebook instance. After the notebook instance is stopped, click **Start** to restart the notebook instance and open it. The instance will have preserved all the spaces for the variables that were unable to run.
