:original_name: modelarts_13_0118.html

.. _modelarts_13_0118:

Why Cannot the Path of a Text File Generated in Windows OS Be Found In a Notebook Instance?
===========================================================================================

Symptom
-------

When a text file generated in Windows is used in a notebook instance, the text content cannot be read and an error message may be displayed indicating that the path cannot be found.

Possible Causes
---------------

The notebook instance runs Linux and its line feed format (CRLF) differs from that (LF) in Windows.

Solution
--------

Convert the file format to Linux in your notebook instance.

Shell:

.. code-block::

   dos2unix  File name
