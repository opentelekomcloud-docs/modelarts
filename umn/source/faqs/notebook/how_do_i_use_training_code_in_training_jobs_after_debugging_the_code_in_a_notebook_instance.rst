:original_name: modelarts_21_0066.html

.. _modelarts_21_0066:

How Do I Use Training Code in Training Jobs After Debugging the Code in a Notebook Instance?
============================================================================================

After the training code is debugged in a notebook instance, if you need to use the training code for training jobs on ModelArts, convert the **ipynb** file into a Python file.

On the Jupyter page, click **Convert to Python File** to convert the training code to a Python file (**.py** file). After the conversion is completed, manually upload the Python file to OBS. Then, select the OBS path in the ModelArts training job to use the training code.


.. figure:: /_static/images/en-us_image_0000001279825389.png
   :alt: **Figure 1** Converting the **.ipynb** file into a Python file

   **Figure 1** Converting the **.ipynb** file into a Python file
