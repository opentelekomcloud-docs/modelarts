:original_name: modelarts_05_0100.html

.. _modelarts_05_0100:

What Do I Do If a Conflict Occurs in the Python Dependency Package of a Custom Prediction Script When I Deploy a Real-Time Service?
===================================================================================================================================

Before importing a model, save the inference code and configuration file in the model folder. When coding with Python, import custom packages in relative import (Python import) mode.

If there are packages with duplicate names in the ModelArts inference framework code and they are imported not in relative import mode, a conflict will occur, leading to a service deployment or prediction failure.
