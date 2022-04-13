.. _modelarts_08_0005:

Overview
========

When you use ExeML, data management, notebook instances, training jobs, models, and services, ModelArts may need to access dependent services such as OBS and Software Repository for Container (SWR). If ModelArts is not authorized to access the services, these functions cannot be used.

You can configure access authorization in either of the following ways:

-  **Using an agency** (recommended)

   After agency authorization is configured, the dependent service operation permissions are delegated to ModelArts so that ModelArts can use the dependent services and perform operations on resources on your behalf.

-  **Using the access key**

   You can use the obtained access key pair (AK/SK) to authorize ModelArts to access dependent services and and perform operations on resources.

Precautions
-----------

-  Agency authorization grants ModelArts permissions on dependent services, such as OBS and SWR. If the OBS permissions are not configured for an IAM user, the user still does not have the permission to operate the services.
-  For users who have used ModelArts before, access key authorization has been configured and does not need to be configured again. However, you are advised to use agency authorization again.
-  For new users, use agency authorization.
