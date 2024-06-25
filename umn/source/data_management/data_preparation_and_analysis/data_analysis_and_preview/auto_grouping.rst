:original_name: dataprepare-modelarts-0022.html

.. _dataprepare-modelarts-0022:

Auto Grouping
=============

To improve the precision of auto labeling algorithms, you can evenly label multiple classes. ModelArts provides built-in grouping algorithms. You can enable auto grouping to improve data labeling efficiency.

Auto grouping can be understood as data labeling preprocessing. Clustering algorithms are used to cluster unlabeled images, and images are labeled or cleaned by group based on the clustering result.

For example, a user searches for *XX* through a search engine, downloads and uploads related images to the dataset, and then uses the auto grouping function to classify *XX* images, such as papers, posters, images confirmed as *XX*, and others. The user can quickly remove unwanted images from a group or select all images of a type and add labels to the images.

.. note::

   Only datasets of image classification, object detection, and image segmentation types support the auto grouping function.

Starting Auto Grouping Tasks
----------------------------

#. Log in to the ModelArts management console. In the navigation pane on the left, choose **Data Management** > **Label Data**.
#. In the labeling job list, select a labeling job of the object detection or image classification type and click the labeling job name to go to the labeling job details page.
#. In the **All statuses** tab of the dataset details page, choose **Auto Grouping** > **Start Task**.

   .. note::

      You can start auto group tasks or view task history only in the **All** tab.

#. In the displayed **Auto Grouping** dialog box, set parameters and click **OK**.

   -  **Groups**: Enter an integer from 2 to 200. The parameter value indicates the number of groups into which images are divided.
   -  **Result Processing Method**: Select **Update attribute** or **Save to OBS**.
   -  **Attribute Name**: If you select **Update attribute**, you need to enter an attribute name.
   -  **Result Storage Path**: If you select **Save to OBS**, specify an OBS path.
   -  **Advanced Feature Settings**: After this function is enabled, you can select **Clarity**, **Brightness**, and **Color** dimensions for the auto grouping function so that the grouping is based on the image brightness, color, and clarity. You can select multiple options.

#. After the task is submitted, the task progress is displayed in the upper right corner of the page. After the task is complete, you can view the history of the auto grouping tasks to learn task status.

Viewing the Auto Grouping Result
--------------------------------

In the **All** tab of the dataset details page, expand **Filter Criteria**, set **Sample Attribute** to the attribute name of the auto grouping task, and set the sample attribute value to filter the grouping result.

Viewing Auto Grouping Task History
----------------------------------

In the **All** tab of the dataset details page, choose **Auto Grouping** > **View Task History**. In the **View Task History** dialog box, basic information about the auto grouping tasks of the current dataset is displayed.
