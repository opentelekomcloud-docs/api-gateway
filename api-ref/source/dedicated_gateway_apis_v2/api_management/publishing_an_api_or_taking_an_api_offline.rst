:original_name: CreateOrDeletePublishRecordForApiV2.html

.. _CreateOrDeletePublishRecordForApiV2:

Publishing an API or Taking an API Offline
==========================================

Function
--------

This API is used to publish an API or take an API offline.

An API can be called only in an environment where the API has been published. APIs that have not been published cannot be called.

You can remove an API from an environment in which it has been published. After this operation, the API can no longer be called in the environment.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/apis/action

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                        |
   +=================+=================+=================+====================================================================+
   | action          | Yes             | String          | Operation to perform.                                              |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | -  online: publish APIs                                            |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | -  offline: take APIs offline                                      |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | Enumeration values:                                                |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | -  **online**                                                      |
   |                 |                 |                 |                                                                    |
   |                 |                 |                 | -  **offline**                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
   | env_id          | Yes             | String          | ID of the environment in which the API will be published.          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
   | api_id          | Yes             | String          | ID of the API to be published or taken offline.                    |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+
   | remark          | No              | String          | Description about the publishing. It cannot exceed 255 characters. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

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

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Publishing an API in an environment

.. code-block::

   {
     "action" : "online",
     "api_id" : "5f918d104dc84480a75166ba99efff21",
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "api_id" : "5f918d104dc84480a75166ba99efff21",
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
     "publish_id" : "9191cdb430724d4b8586ed7f1b962ca2",
     "publish_time" : "2020-08-03T01:36:00.592970615Z",
     "version_id" : "ee1a5a38d3d3493abf1dc4ed6cacfa0b"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:action. Please refer to the support documentation"
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

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "APIG.3002",
     "error_msg" : "API 5f918d104dc84480a75166ba99efff21 does not exist"
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
201         Created
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
