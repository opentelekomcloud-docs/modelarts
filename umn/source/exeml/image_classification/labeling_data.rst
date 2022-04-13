.. _modelarts_21_0005:

Labeling Data
=============

Model training requires a large number of labeled images. Therefore, before model training, add labels to the images that are not labeled. ModelArts allows you to add labels in batches by one click. You can also modify or delete labels that have been added to images. Prepare at least two classes of images for training. Each class contains at least five images. To achieve better effect, prepare at least 50 images for each class. If the image classes are similar, more images are required.

Labeling Images
---------------

#. On the **Label Data** tab page, click the **Unlabeled** tab. All unlabeled images are displayed. Select the images to be labeled in sequence, or tick **Select Current Page** to select all images on the page, and then add labels to the images in the right pane.
#. After selecting an image, input a label in the **Label** text box, or select an existing label from the drop-down list. Click **OK**. The selected image is labeled. For example, you can select multiple images containing tulips and add label **tulips** to them. Then select other unlabeled images and label them as **sunflowers** and **roses**. After the labeling is complete, the images are saved on the **Labeled** tab page.

   a. You can add multiple labels to an image.
   b. A label name can contain a maximum of 32 characters, including Chinese characters, letters, digits, hyphens (-), and underscores (_).

#. After all the images are labeled, view them on the **Labeled** tab page or view **All Labels** in the right pane to check the name and quantity of the labels.

Synchronizing or Adding Images
------------------------------

On the **ExeML** page, click the project name. The **Label Data** tab page is displayed. When creating a project, you can add images from a local PC or synchronize image data from OBS.

-  **Add Image**: You can quickly add images on a local PC to ModelArts and synchronize the images to the OBS path specified during project creation. Click **Add Image**. In the dialog box that is displayed, click **Add Image** and add images. The total size of all images uploaded in one attempt cannot exceed 8 MB. The size of a single image cannot exceed 5 MB.
-  **Synchronize Data Source**: You can upload images to the OBS directory specified during project creation and click **Synchronize Data Source** to quickly add the images in the OBS directory to ModelArts.
-  **Delete Image**: You can delete images one by one, or tick **Select Current Page** to delete all images on the page.

   .. note::

      The deleted images cannot be recovered. Exercise caution when performing this operation.

Modifying Labeled Data
----------------------

After labeling data, you can modify the labeled data on the **Labeled** tab page.

-  **Modifying based on images**

   On the data labeling page, click the **Labeled** tab, and select one or more images to be modified from the image list. Modify the image information in the label information area on the right.

   -  Adding a label: In the **Label** text box, select an existing label, or enter a new label name and click **OK** to add the label to the selected image.
   -  Modifying a label: In the **File Labels** area, click the editing icon in the **Operation** column, enter the correct label name in the text box, and click the check mark icon to complete the modification.
   -  Deleting a label: In the **Labels of Selected Image** area, click |image1| in the **Operation** column to delete the label.

-  **Modifying based on labels**

   On the dataset labeling page, click the **Labeled** tab. The information about all labels is displayed on the right.

   -  Modifying a label: Click the editing icon in the **Operation** column. In the dialog box that is displayed, enter the new label name and click **OK**. After the modification, the images that have been added with the label use the new label name.
   -  Deleting a label: Click the deletion icon in the **Operation** column. In the displayed dialog box, select **Delete label**, **Delete label and images with only the label (Do not delete source files)**, or **Delete label and images with only the label (Delete source files)**, and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001110760936.png

