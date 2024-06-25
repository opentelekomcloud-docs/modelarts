:original_name: modelarts_05_3205.html

.. _modelarts_05_3205:

Can Two Accounts Concurrently Label One Dataset?
================================================

Multiple accounts (annotators) are allowed to concurrently label one dataset. However, if multiple annotators concurrently label one image, only the labeling of the last annotator will be used as the labeling result. It is a good practice to label one image by multiple annotators in turn and save the labeling result of each annotator promptly.
