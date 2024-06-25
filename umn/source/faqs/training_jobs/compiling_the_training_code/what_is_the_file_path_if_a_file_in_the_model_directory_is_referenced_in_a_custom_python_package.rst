:original_name: modelarts_05_3217.html

.. _modelarts_05_3217:

What Is the File Path If a File in the model Directory Is Referenced in a Custom Python Package?
================================================================================================

To obtain the actual path to a file in a container, use Python.

.. code-block::

   os.getcwd() # Obtain the current work directory (absolute path) of the file.
   os.path.realpath(__ file __) # Obtain the absolute path of the file.

You can also use other methods of obtaining a file path through the search engine and use the obtained path to read and write the file.
