:original_name: modelarts_05_0254.html

.. _modelarts_05_0254:

How Do I Merge Two Datasets?
============================

Datasets cannot be merged.

However, you can perform the following operations to merge the data of two datasets into one dataset.

For example, to merge datasets A and B, do the following:

#. Publish datasets A and B.

#. Obtain the manifest files of the two datasets from the OBS path set for **Output Dataset Path**.

#. Create empty dataset C and select an empty OBS folder for **Input Dataset Path**.

#. Import the manifest files of datasets A and B to dataset C.

   After the import is complete, data in datasets A and B is merged into dataset C. To use the merged dataset, publish dataset C.
