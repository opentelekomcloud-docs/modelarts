.. _ListProcessorTaskVersionResults:

Querying the Result of a Data Processing Task Version
=====================================================

Function
--------

This API is used to query the result of a data processing task version.

URI
---

GET /v2/{project_id}/processor-tasks/{task_id}/versions/{version_id}/results

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                        |
   +============+===========+========+====================================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain the project ID, see :ref:`Obtaining a Project ID <modelarts_03_0147>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | task_id    | Yes       | String | ID of a data processing task.                                                                                      |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+
   | version_id | Yes       | String | Version ID of a data processing task.                                                                              |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                                                                         |
   +===================+=================+=================+=====================================================================================================================================================================================================================================+
   | limit             | No              | Integer         | Maximum number of records returned on each page. The value ranges from 1 to 100. The default value is **10**.                                                                                                                       |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset            | No              | Integer         | Start page of the paging list. The default value is **0**.                                                                                                                                                                          |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | process_parameter | No              | String          | Image resizing setting, which is the same as the OBS resizing setting. For details, see . For example, **image/resize,m_lfit,h_200** indicates that the target image is resized proportionally and the height is set to 200 pixels. |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | result_property   | No              | String          | Sample status. If this parameter is not delivered or is set to **-1**, all samples are returned by default. The options are as follows:                                                                                             |
   |                   |                 |                 |                                                                                                                                                                                                                                     |
   |                   |                 |                 | -  **-1**: all                                                                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                                                                     |
   |                   |                 |                 | -  **0**: reserve                                                                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                                                                     |
   |                   |                 |                 | -  **1**: modify                                                                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                                                     |
   |                   |                 |                 | -  **2**: delete                                                                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                                                                     |
   |                   |                 |                 | -  **3**: add                                                                                                                                                                                                                       |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | Parameter | Type                                                                                                                                        | Description                       |
   +===========+=============================================================================================================================================+===================================+
   | count     | Integer                                                                                                                                     | Total number of results.          |
   +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | has_more  | Boolean                                                                                                                                     | Whether all results are returned. |
   +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+
   | results   | Array of :ref:`DescProcessorTaskVersionResultsResp <listprocessortaskversionresults__response_descprocessortaskversionresultsresp>` objects | Result displayed by page.         |
   +-----------+---------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------+

.. _listprocessortaskversionresults__response_descprocessortaskversionresultsresp:

.. table:: **Table 4** DescProcessorTaskVersionResultsResp

   +-----------------------+-----------------------+------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                |
   +=======================+=======================+============================================================+
   | new_source            | String                | Address of the sample after processing.                    |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | origin_source         | String                | Source address of a sample.                                |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | result_description    | Array of objects      | Processing description of a sample.                        |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | result_property       | Integer               | Processing status of a sample. The options are as follows: |
   |                       |                       |                                                            |
   |                       |                       | -  **-1**: all                                             |
   |                       |                       |                                                            |
   |                       |                       | -  **0**: reserve                                          |
   |                       |                       |                                                            |
   |                       |                       | -  **1**: modify                                           |
   |                       |                       |                                                            |
   |                       |                       | -  **2**: delete                                           |
   |                       |                       |                                                            |
   |                       |                       | -  **3**: add                                              |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | sample_id             | String                | Sample ID, which is generated by **md5** in the OBS path.  |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | signed_new_source     | String                | Address of the processed sample after signature.           |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | signed_origin_source  | String                | Source sample address after signature.                     |
   +-----------------------+-----------------------+------------------------------------------------------------+
   | version_id            | String                | Version ID of a data processing task.                      |
   +-----------------------+-----------------------+------------------------------------------------------------+

Example Requests
----------------

Querying the Result of a Data Processing Task Version

.. code-block::

   GET https://{endpoint}/v2/{project_id}/processor-tasks/{task_id}/versions/{version_id}/results?offset=0&limit=14&result_property=-1

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "count" : 3,
     "results" : [ {
       "sample_id" : "0ac9aee517acbef965f547bb5a3268af",
       "version_id" : "7PoIhUzSk92OglQrTxr",
       "origin_source" : "s3://test-obs/classify/data/cat-dog/8.jpg",
       "new_source" : "obs://test-obs/classify/output/7PoIhUzSk92OglQrTxr/Data/8.jpg",
       "signed_origin_source" : "https://test-obs.obs.xxx.com:443/classify/data/cat-dog/8.jpg?AccessKeyId=I5IZ9R29S1W9WACNJJ0J&Expires=1606380154&x-obs-security-token=gQpjbi1ub3J0aC03jQ5yFSR1TfKXjeawutgyAnMrdoGNaSkeSBOKK...&Signature=GbnVBZ5JxUWhiAulUzpV9TD835Q%3D",
       "signed_new_source" : "https://test-obs.obs.xxx.com:443/classify/output/7PoIhUzSk92OglQrTxr/Data/8.jpg?AccessKeyId=I5IZ9R29S1W9WACNJJ0J&Expires=1606380154&x-obs-security-token=gQpjbi1ub3J0aC03jQ5yFSR1TfKXjeawutgyAnMrdoGNaSkeSBOKK...&Signature=Q5stFFFfVx9kykR49S8PPBlFqe0%3D",
       "result_property" : 3,
       "result_description" : [ [ "use AddNoise augmentation" ], [ "result_description to translate" ] ]
     }, {
       "sample_id" : "196799b2d731727b1800b70851fc60b0",
       "version_id" : "7PoIhUzSk92OglQrTxr",
       "origin_source" : "s3://test-obs/classify/data/cat-dog/2.jpg",
       "new_source" : "obs://test-obs/classify/output/7PoIhUzSk92OglQrTxr/Data/2.jpg",
       "signed_origin_source" : "https://test-obs.obs.xxx.com:443/classify/data/cat-dog/2.jpg?AccessKeyId=QEKFB6WFGZWC2YUP2JPK&Expires=1606380154&x-obs-security-token=gQpjbi1ub3J0aC03jdUZcXVRCNOHjWNNWiuu2E9Q...&Signature=6yvhJufi5kQO6UjToQgR0ztP%2Bis%3D",
       "signed_new_source" : "https://test-obs.obs.xxx.com:443/classify/output/7PoIhUzSk92OglQrTxr/Data/2.jpg?AccessKeyId=QEKFB6WFGZWC2YUP2JPK&Expires=1606380154&x-obs-security-token=gQpjbi1ub3J0aC03jdUZcXVRCNOHjWNNWiuu2E...&Signature=Zr%2BAEBDJwKS%2FpS6vzxK7MSzjblA%3D",
       "result_property" : 3,
       "result_description" : [ [ "use AddNoise augmentation" ], [ "result_description to translate" ] ]
     }, {
       "sample_id" : "1dc7351b78dcb24850f71d20267edd0e",
       "version_id" : "7PoIhUzSk92OglQrTxr",
       "origin_source" : "s3://test-obs/classify/data/cat-dog/import_1603716822103/test-obs/classify/output/E8ZLnTQvPBVtbZ6QsAp/Data/13.jpg",
       "new_source" : "obs://test-obs/classify/output/7PoIhUzSk92OglQrTxr/Data/13.jpg",
       "signed_origin_source" : "https://test-obs.obs.xxx.com:443/classify/data/cat-dog/import_1603716822103/test-obs/classify/output/E8ZLnTQvPBVtbZ6QsAp/Data/13.jpg?AccessKeyId=W6TSX9F1BRS8AUBDYKPY&Expires=1606380154&x-obs-security-token=gQpjbi1ub3J0aC03jVVFic8iObvdqZLuWxyIHlAjbJPCTX...&Signature=WV73XnoMkBDoSuVe%2BFSUaP1GxKw%3D",
       "signed_new_source" : "https://test-obs.obs.xxx.com:443/classify/output/7PoIhUzSk92OglQrTxr/Data/13.jpg?AccessKeyId=W6TSX9F1BRS8AUBDYKPY&Expires=1606380154&x-obs-security-token=gQpjbi1ub3J0aC03jVVFic8iObvdqZLuWxyIHlAjbJPCTXeYXkQh8z...&Signature=%2FYsgrsbyrz5ZQrndrQ9QyoHluYQ%3D",
       "result_property" : 3,
       "result_description" : [ [ "use AddNoise augmentation" ], [ "result_description to translate" ] ]
     } ],
     "has_more" : true
   }

Status Codes
------------

=========== ============
Status Code Description
=========== ============
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
=========== ============

Error Codes
-----------

See :ref:`Error Codes <modelarts_03_0095>`.
