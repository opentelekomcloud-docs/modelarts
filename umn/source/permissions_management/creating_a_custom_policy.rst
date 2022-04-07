.. _modelarts_23_0080:

Creating a Custom Policy
========================

If default policies cannot meet the requirements on fine-grained access control, you can create custom policies and assign the policies to the user group.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For details about how to create a custom policy, see section "Creating a Custom Policy" in the *Identity and Access Management User Guide*. This section describes :ref:`example custom policies of OBS (a dependent service of ModelArts) <modelarts_23_0080__en-us_topic_0284259054_en-us_topic_0170867515_section3734428121013>` and :ref:`ModelArts <modelarts_23_0080__en-us_topic_0284259054_en-us_topic_0170867515_section1493518251395>`.

Precautions
-----------

-  The permissions to use ModelArts depend on OBS authorization. Therefore, you need to grant OBS system permissions to users.
-  A custom policy can contain actions of multiple services that are globally accessible or accessible through region-specific projects.
-  To define permissions required to access both global and project-level services, create two custom policies and specify the scope as **Global services** and **Project-level services**. Then grant the two policies to the users.

.. _modelarts_23_0080__en-us_topic_0284259054_en-us_topic_0170867515_section3734428121013:

Example Custom Policies of OBS
------------------------------

ModelArts is a project-level service, and OBS is a global service. Therefore, you need to create custom policies for the two services respectively and grant them to users. The permissions to use ModelArts depend on OBS authorization. The following example shows the minimum permissions for OBS, including the permissions for OBS buckets and objects. After being granted the minimum permissions for OBS, users can access OBS from ModelArts without restrictions.

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
           {
               "Action": [
                   "obs:bucket:ListAllMybuckets",
                   "obs:bucket:HeadBucket",
                   "obs:bucket:ListBucket",
                   "obs:bucket:GetBucketLocation",
                   "obs:object:GetObject",
                   "obs:object:GetObjectVersion",
                   "obs:object:PutObject",
                   "obs:object:DeleteObject",
                   "obs:object:DeleteObjectVersion",
                   "obs:object:ListMultipartUploadParts",
                   "obs:object:AbortMultipartUpload",
                   "obs:object:GetObjectAcl",
                   "obs:object:GetObjectVersionAcl",
                   "obs:bucket:PutBucketAcl"
               ],
               "Effect": "Allow"
           }
       ]
   }

.. _modelarts_23_0080__en-us_topic_0284259054_en-us_topic_0170867515_section1493518251395:

Example Custom Policies of ModelArts
------------------------------------

-  Example: Denying ExeML project deletion

   A deny policy must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both Allow and Deny actions, the Deny actions take precedence over the Allow actions.

   The following method can be used if you need to assign permissions of the **ModelArts FullAccess** policy to a user but also forbid the user from deleting ExeML projects. Create a custom policy for denying ExeML project deletion, and assign both policies to the group the user belongs to. Then the user can perform all operations on ModelArts except deleting ExeML projects. The following is an example deny policy:

   .. code-block::

      { 
            "Version": "1.1", 
            "Statement": [ 
                  { 
                "Effect": "Deny", 
                        "Action": [ 
                              "modelarts:exemlProject:delete" 
                        ] 
                  } 
            ] 
      }

-  Example: Allowing users to use only development environments

   The following is a policy configuration example for this user:

   .. code-block::

      { 
          "Version": "1.1", 
          "Statement": [ 

              { 
                  "Effect": "Allow", 
                  "Action": [ 
                      "modelarts:notebook:list", 
                      "modelarts:notebook:create" ,
                      "modelarts:notebook:get" ,
                      "modelarts:notebook:update" ,
                      "modelarts:notebook:delete" ,
                      "modelarts:notebook:action" ,
                      "modelarts:notebook:access" 
                  ] 
              } 
          ] 
      }
