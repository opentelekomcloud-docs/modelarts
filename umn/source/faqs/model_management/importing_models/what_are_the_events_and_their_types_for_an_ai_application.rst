:original_name: modelarts_06_0008.html

.. _modelarts_06_0008:

What Are the Events and Their Types for an AI application?
==========================================================

During the creation of an AI application, every key event is automatically recorded. You can view the events on the details page of the AI application at any time.

The following table lists the events, based on which you can locate faults occurred during AI application creation.

+----------+-------------------------------------------------------------------------------------------------------------------------+
| Type     | Event (*xxx* should be replaced with the actual value.)                                                                 |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The model starts to import.                                                                                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to create the image.                                                                                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | The custom image does not support specified dependencies.                                                               |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Only custom images support **swr_location**.                                                                            |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | The health check API of a custom image must be *xxx*.                                                                   |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The image creation task is in the *xxx* state.                                                                          |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Label *xxx* does not exist in image *xxx*.                                                                              |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Invalid parameter value *xxx* exists in the model configuration file.                                                   |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to obtain the labels of image *xxx*.                                                                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to import data because *xxx* is larger than *xxx* GB.                                                            |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | User *xxx* does not have OBS permission obs:object:PutObjectAcl.                                                        |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Creating the image timed out. The timeout duration is *xxx* minutes.                                                    |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Model description updated.                                                                                              |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Model runtime dependencies not updated.                                                                                 |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Model runtime dependencies updated. Recreating the image.                                                               |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | SWR traffic control triggered. Try again later.                                                                         |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The system is being upgraded. Try again later.                                                                          |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to obtain the source image. An error occurred in authentication. The token has expired.                          |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to obtain the source image. Check whether the image exists.                                                      |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Source image size calculated.                                                                                           |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Source image shared.                                                                                                    |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to create the image due to traffic control. Try again later.                                                     |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to send the image creation request.                                                                              |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to share the source image. Check whether the image exists or whether you have the permission to share the image. |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The model imported.                                                                                                     |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Model file imported.                                                                                                    |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Model size calculated.                                                                                                  |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to import the model.                                                                                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to copy the model file. Check whether you have the OBS permission.                                               |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to schedule the image creation task.                                                                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to start the image creation task.                                                                                |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | The Roman image has been created but cannot be shared with resource tenants.                                            |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | Image created.                                                                                                          |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The image creation task started.                                                                                        |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The environment image creation task started.                                                                            |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The request for creating an environment image received.                                                                 |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | The request for creating an image received.                                                                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Normal   | An existing environment image is used.                                                                                  |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to create the image. For details, see image creation logs.                                                       |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to create the image due to an internal system error. Contact technical support.                                  |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to create the OBS bucket due to an internal system error. Contact technical support.                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to calculate the model size. Subpath *xxx* does not exist in path *xxx*.                                         |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to calculate the model size. The model of the *xxx* type does not exist in path *xxx*.                           |
+----------+-------------------------------------------------------------------------------------------------------------------------+
| Abnormal | Failed to calculate the model size. More than one *xxx* model file is stored in path *xxx*.                             |
+----------+-------------------------------------------------------------------------------------------------------------------------+

During AI application creation, key events can both be manually and automatically refreshed.

Viewing Events
--------------

#. In the navigation pane of the ModelArts management console, choose **AI Application Management** > **AI Applications**. In the AI application list, click the name of the target AI application to go to its details page.
#. View the events on the **Events** tab page.
