.. _modelarts_05_0100:

What Should I Do If a Conflict Occurs When Deploying a Model As a Real-Time Service?
====================================================================================

Before importing a model, you need to place the corresponding inference code and configuration file in the model folder. When encoding with Python, you are advised to use a relative import (Python import) to import custom packages.

If the relative import mode is not used, a conflict will occur once a package with the same name exists in a real-time service. As a result, model deployment or prediction fails.
