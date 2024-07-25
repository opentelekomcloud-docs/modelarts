:original_name: modelarts_05_0168.html

.. _modelarts_05_0168:

Why Does the Notebook Instance Break Down When opencv.imshow Is Used?
=====================================================================

Symptom
-------

When opencv.imshow is used in a notebook instance, the notebook instance breaks down.

Possible Causes
---------------

The cv2.imshow function in OpenCV malfunctions in a client/server environment such as Jupyter. However, Matplotlib does not have this problem.

Solution
--------

Display images by referring to the following example. Note that OpenCV displays BGR images while Matplotlib displays RGB images.

Python:

::

   from matplotlib import pyplot as plt
   import cv2
   img = cv2.imread('Image path')
   plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
   plt.title('my picture')
   plt.show()
