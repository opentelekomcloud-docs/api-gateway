:original_name: BatchPublishOrOfflineApiV2.html

.. _BatchPublishOrOfflineApiV2:

Publishing APIs or Taking APIs Offline
======================================

Function
--------

This API is used to publish multiple APIs in an environment or to remove multiple APIs from the environment in which they have been published.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/apis/publish

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------+
   | Parameter       | Mandatory       | Type            | Description                   |
   +=================+=================+=================+===============================+
   | action          | Yes             | String          | -  online: publish APIs       |
   |                 |                 |                 |                               |
   |                 |                 |                 | -  offline: take APIs offline |
   +-----------------+-----------------+-----------------+-------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                            |
   +=================+=================+==================+========================================================================================================================================+
   | apis            | No              | Array of strings | IDs of APIs to be published or taken offline. A maximum of 1000 APIs are allowed at a time. Either apis or group_id must be specified. |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | Yes             | String           | Environment ID.                                                                                                                        |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | No              | String           | API group ID. Either apis or group_id must be specified.                                                                               |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | remark          | No              | String           | Description of the publication.                                                                                                        |
   |                 |                 |                  |                                                                                                                                        |
   |                 |                 |                  | It cannot exceed 255 characters.                                                                                                       |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | Parameter | Type                                                                                     | Description                                                        |
   +===========+==========================================================================================+====================================================================+
   | success   | Array of :ref:`PublishResp <batchpublishorofflineapiv2__response_publishresp>` objects   | Message for successful API publication or taking offline.          |
   +-----------+------------------------------------------------------------------------------------------+--------------------------------------------------------------------+
   | failure   | Array of :ref:`BatchFailure <batchpublishorofflineapiv2__response_batchfailure>` objects | Error message and APIs that fail to be published or taken offline. |
   +-----------+------------------------------------------------------------------------------------------+--------------------------------------------------------------------+

.. _batchpublishorofflineapiv2__response_publishresp:

.. table:: **Table 6** PublishResp

   +--------------+--------+------------------------------------------------------------+
   | Parameter    | Type   | Description                                                |
   +==============+========+============================================================+
   | publish_id   | String | Publication record ID.                                     |
   +--------------+--------+------------------------------------------------------------+
   | api_id       | String | API ID.                                                    |
   +--------------+--------+------------------------------------------------------------+
   | api_name     | String | API name.                                                  |
   +--------------+--------+------------------------------------------------------------+
   | env_id       | String | ID of the environment in which the API has been published. |
   +--------------+--------+------------------------------------------------------------+
   | remark       | String | Description about the publication.                         |
   +--------------+--------+------------------------------------------------------------+
   | publish_time | String | Publication time.                                          |
   +--------------+--------+------------------------------------------------------------+
   | version_id   | String | API version currently in use.                              |
   +--------------+--------+------------------------------------------------------------+

.. _batchpublishorofflineapiv2__response_batchfailure:

.. table:: **Table 7** BatchFailure

   +------------+--------+-------------------------------------------------------------+
   | Parameter  | Type   | Description                                                 |
   +============+========+=============================================================+
   | api_id     | String | ID of an API that fails to be published or taken offline.   |
   +------------+--------+-------------------------------------------------------------+
   | api_name   | String | Name of an API that fails to be published or taken offline. |
   +------------+--------+-------------------------------------------------------------+
   | error_code | String | Error code.                                                 |
   +------------+--------+-------------------------------------------------------------+
   | error_msg  | String | Error message.                                              |
   +------------+--------+-------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

.. code-block::

   {
     "apis" : [ "3a955b791bd24b1c9cd94c745f8d1aad", "abd9c4b2ff974888b0ba79be7e6b2762" ],
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
     "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
     "remark" : "Published to the production environment"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "success" : [ {
       "publish_id" : "9f27d1dc4f4242a9abf88e563dbfc33d",
       "api_id" : "3a955b791bd24b1c9cd94c745f8d1aad",
       "api_name" : "Api_mock",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "version_id" : "632b2c9e022941969af9a1d45735ae2c",
       "remark" : "Published to the production environment",
       "publish_time" : "2020-08-03T03:01:31.26522821Z"
     } ],
     "failure" : [ {
       "api_id" : "abd9c4b2ff974888b0ba79be7e6b2762",
       "error_code" : "APIG.3002",
       "error_msg" : "Api abd9c4b2ff974888b0ba79be7e6b2762 not found"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value: parameter action should be \\\"online\\\" or \\\"offline\\\""
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "APIG.1002",
     "error_msg" : "Incorrect token or token resolution failed"
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "APIG.1005",
     "error_msg" : "No permissions to request this method"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIG.9999",
     "error_msg" : "System error"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
