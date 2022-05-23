:original_name: modelarts_03_0234.html

.. _modelarts_03_0234:

ExeML Permissions
=================

ExeML APIs are inaccessible to external systems. To use ExeML functions on the console and manage permissions, perform the operations described in the following table.

.. table:: **Table 1** Refined ExeML permissions

   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Permission                                   | Action                               | IAM Project | Enterprise Project |
   +==============================================+======================================+=============+====================+
   | Obtaining the List of ExeML Projects         | modelarts:exemlProject:list          | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Creating an ExeML Project                    | modelarts:exemlProject:create        | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Deleting an ExeML Project                    | modelarts:exemlProject:delete        | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Creating an ExeML Prediction Version         | modelarts:exemlProjectInf:create     | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Updating the Description of an ExeML Project | modelarts:exemlProject:update        | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Creating an ExeML Training Job Version       | modelarts:exemlProjectTrain:create   | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Viewing ExeML Projects                       | modelarts:exemlProject:get           | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Checking the ExeML Version                   | modelarts:exemlProject:get           | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Deleting an ExeML Training Job Version       | modelarts:exemlProjectVersion:delete | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
   | Stopping an ExeML Prediction Job Version     | modelarts:exemlProjectVersion:delete | Y           | Y                  |
   +----------------------------------------------+--------------------------------------+-------------+--------------------+
