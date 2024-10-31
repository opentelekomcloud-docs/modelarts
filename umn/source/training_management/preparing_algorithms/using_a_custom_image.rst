:original_name: develop-modelarts-0077.html

.. _develop-modelarts-0077:

Using a Custom Image
====================

The subscribed algorithms and preset images can be used in most training scenarios. In certain scenarios, ModelArts allows you to create custom images to train models.

Customizing an image requires a deep understanding of containers. Use this method only if the subscribed algorithms and preset images cannot meet your requirements. Custom images can be used to train models in ModelArts only after they are uploaded to the Software Repository for Container (SWR).

You can use custom images for training on ModelArts in either of the following ways:

-  Using a preset image with customization

   If you use a preset image to create a training job and you need to modify or add some software dependencies based on the preset image, you can customize the preset image. In this case, select a preset image and choose **Customize** from the framework version drop-down list box.

-  Using a custom image

   You can create an image based on the ModelArts image specifications, select your own image and configure the code directory (optional) and boot command to create a training job.

Using a Preset Image with Customization
---------------------------------------

The only difference between this method and creating a training job totally based on a preset image is that you must select an image. You can create a custom image based on a preset image.


.. figure:: /_static/images/en-us_image_0000002079176661.png
   :alt: **Figure 1** Creating an algorithm using a preset image with customization

   **Figure 1** Creating an algorithm using a preset image with customization

The process of this method is the same as that of creating a training job based on a preset image. For example:

-  The system automatically injects environment variables.

   -  PATH=${MA_HOME}/anaconda/bin:${PATH}
   -  LD_LIBRARY_PATH=${MA_HOME}/anaconda/lib:${LD_LIBRARY_PATH}
   -  PYTHONPATH=${MA_JOB_DIR}:${PYTHONPATH}

-  The selected boot file will be automatically started using Python commands. Ensure that the Python environment is correct. The **PATH** environment variable is automatically injected. Run the following commands to check the Python version for the training job:

   -  export MA_HOME=/home/ma-user; docker run --rm {image} ${MA_HOME}/anaconda/bin/python -V
   -  docker run --rm {image} $(which python) -V

-  The system automatically adds hyperparameters associated with the preset image.


Using a Custom Image
--------------------


.. figure:: /_static/images/en-us_image_0000002043019012.png
   :alt: **Figure 2** Creating an algorithm using a custom image

   **Figure 2** Creating an algorithm using a custom image

For details about how to use custom images supported by the new-version training, see :ref:`Using a Custom Image to Train Models <docker-modelarts_0017>`.

If all used images are customized, do as follows to use a specified Conda environment to start training:

Training jobs do not run in a shell. Therefore, you are not allowed to run the **conda activate** command to activate a specified Conda environment. In this case, use other methods to start training.

For example, Conda in your custom image is installed in the **/home/ma-user/anaconda3** directory, the Conda environment is **python-3.7.10**, and the training script is stored in **/home/ma-user/modelarts/user-job-dir/code/train.py**. Use a specified Conda environment to start training in one of the following ways:

-  Method 1: Configure the correct **DEFAULT_CONDA_ENV_NAME** and **ANACONDA_DIR** environment variables for the image.

   Run the **python** command to start the training script. The following shows an example:

   .. code-block::

      python /home/ma-user/modelarts/user-job-dir/code/train.py

-  Method 2: Use the path of **conda env python**.

   Run the **/home/ma-user/anaconda3/envs/python-3.7.10/bin/python** command to start the training script. The following shows an example:

   .. code-block::

      /home/ma-user/anaconda3/envs/python-3.7.10/bin/python /home/ma-user/modelarts/user-job-dir/code/train.py

-  Method 3: Configure the **PATH** environment variable.

   Configure the bin directory of the specified Conda environment into the path environment variable. Run the **python** command to start the training script. The following shows an example:

   .. code-block::

      export PATH=/home/ma-user/anaconda3/envs/python-3.7.10/bin:$PATH; python /home/ma-user/modelarts/user-job-dir/code/train.py

-  Method 4: Run the **conda run -n** command.

   Run the **/home/ma-user/anaconda3/bin/conda run -n python-3.7.10** command to execute the training. The following shows an example:

   .. code-block::

      /home/ma-user/anaconda3/bin/conda run -n python-3.7.10 python /home/ma-user/modelarts/user-job-dir/code/train.py

.. note::

   If there is an error indicating that the .so file is unavailable in the **$ANACONDA_DIR/envs/$DEFAULT_CONDA_ENV_NAME/lib** directory, add the directory to **LD_LIBRARY_PATH** and place the following command before the preceding boot command:

   .. code-block::

      export LD_LIBRARY_PATH=$ANACONDA_DIR/envs/$DEFAULT_CONDA_ENV_NAME/lib:$LD_LIBRARY_PATH;

   For example, the example boot command used in method 1 is as follows:

   .. code-block::

      export LD_LIBRARY_PATH=$ANACONDA_DIR/envs/$DEFAULT_CONDA_ENV_NAME/lib:$LD_LIBRARY_PATH; python /home/ma-user/modelarts/user-job-dir/code/train.py
