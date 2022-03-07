Introduction to Team Labeling
=============================

Generally, a small data labeling task can be completed by an individual. However, team work is required to label a large dataset. ModelArts provides the team labeling function. A labeling team can be formed to manage labeling for the same dataset.

|image1|

The team labeling function supports only datasets for image classification, object detection, text classification, named entity recognition, text triplet, and speech paragraph labeling.

How to Enable Team Labeling
---------------------------

-  When creating a dataset, enable **Team Labeling** and select a team or task manager.\ **Figure 1** Enabling during dataset creation
   |image2|
-  If team labeling is not enabled for a dataset that has been created, create a team labeling task to enable team labeling. For details about how to create a team labeling task, see `Creating Team Labeling Tasks <modelarts_23_0210.html#modelarts_23_0210__en-us_topic_0209053802_section72262410214>`__.\ **Figure 2** Creating a team labeling task in a dataset list
   |image3|
   **Figure 3** Creating a team labeling task
   |image4|
   **Figure 4** Creating a team labeling task on the dataset details page
   |image5|

Operations Related to Team Labeling
-----------------------------------

-  `Team Management <modelarts_23_0182.html>`__
-  `Member Management <modelarts_23_0183.html>`__
-  `Managing Team Labeling Tasks <modelarts_23_0210.html>`__


.. |image1| image:: /images/note_3.0-en-us.png
.. |image2| image:: /images/en-us_image_0000001157080899.png

.. |image3| image:: /images/en-us_image_0000001156921451.png

.. |image4| image:: /images/en-us_image_0000001110761582.png

.. |image5| image:: /images/en-us_image_0000001110761054.png

