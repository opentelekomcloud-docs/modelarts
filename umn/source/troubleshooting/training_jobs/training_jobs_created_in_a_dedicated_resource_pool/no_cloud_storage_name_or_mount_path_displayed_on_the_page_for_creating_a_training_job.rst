:original_name: modelarts_trouble_0132.html

.. _modelarts_trouble_0132:

No Cloud Storage Name or Mount Path Displayed on the Page for Creating a Training Job
=====================================================================================

Symptom
-------

On the page for creating a training job, there is no option for the cloud storage and mount path.

Possible Causes
---------------

The network of the target dedicated resource pool is not connected, or no SFS has been created.

Solution
--------

In the dedicated resource pool list, click the ID or name of the target resource pool to go to its details page. Click **Configure NAS VPC** in the upper right corner to check whether NAS VPC has been enabled. If the NAS VPC name and NAS subnet ID on the details page are left blank, NAS VPC is not enabled. In this case, enable NAS VPC.

If an error message is displayed after you attempt to enable it, the possible cause is that a VPC peering connection has been created for the VPC. In this case, delete the VPC peering connection and try again.
