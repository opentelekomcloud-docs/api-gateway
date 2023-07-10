:original_name: ListApisUnbindedToAppV2.html

.. _ListApisUnbindedToAppV2:

Querying APIs Not Bound with an App
===================================

Function
--------

This API is used to query the self-developed APIs to which an app has not been bound in a specified environment.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/app-auths/unbinded-apis

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================+
   | offset          | No              | Long            | Offset from which the query starts. If the value is less than 0, it is automatically converted to 0.                                                                                |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Default: **0**                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of items displayed on each page. A value less than or equal to 0 will be automatically converted to 20, and a value greater than 500 will be automatically converted to 500. |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Maximum: **500**                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Default: **20**                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_id          | Yes             | String          | App ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | Yes             | String          | Environment ID.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | No              | String          | API group ID.                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_id          | No              | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_name        | No              | String          | API name.                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-----------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                              | Description                                          |
   +===========+===================================================================================+======================================================+
   | size      | Integer                                                                           | Length of the returned resource list.                |
   +-----------+-----------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                              | Number of resources that match the query conditions. |
   +-----------+-----------------------------------------------------------------------------------+------------------------------------------------------+
   | apis      | Array of :ref:`ApiOutline <listapisunbindedtoappv2__response_apioutline>` objects | API list.                                            |
   +-----------+-----------------------------------------------------------------------------------+------------------------------------------------------+

.. _listapisunbindedtoappv2__response_apioutline:

.. table:: **Table 5** ApiOutline

   +--------------+--------+--------------------------------------------------------------+
   | Parameter    | Type   | Description                                                  |
   +==============+========+==============================================================+
   | auth_type    | String | API authentication mode.                                     |
   +--------------+--------+--------------------------------------------------------------+
   | run_env_name | String | Name of the environment in which the API has been published. |
   +--------------+--------+--------------------------------------------------------------+
   | group_name   | String | Name of the API group to which the API belongs.              |
   +--------------+--------+--------------------------------------------------------------+
   | publish_id   | String | Publication record ID.                                       |
   +--------------+--------+--------------------------------------------------------------+
   | group_id     | String | ID of the API group to which the API belongs.                |
   +--------------+--------+--------------------------------------------------------------+
   | name         | String | API name.                                                    |
   +--------------+--------+--------------------------------------------------------------+
   | remark       | String | API description.                                             |
   +--------------+--------+--------------------------------------------------------------+
   | run_env_id   | String | ID of the environment in which the API has been published.   |
   +--------------+--------+--------------------------------------------------------------+
   | id           | String | API ID.                                                      |
   +--------------+--------+--------------------------------------------------------------+
   | req_uri      | String | API request address.                                         |
   +--------------+--------+--------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 2,
     "size" : 2,
     "apis" : [ {
       "auth_type" : "APP",
       "run_env_name" : "",
       "group_name" : "api_group_001",
       "publish_id" : "",
       "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
       "name" : "Api_function",
       "remark" : "FunctionGraph backend API",
       "run_env_id" : "",
       "id" : "abd9c4b2ff974888b0ba79be7e6b2763",
       "req_uri" : "/test/function"
     }, {
       "auth_type" : "APP",
       "run_env_name" : "RELEASE",
       "group_name" : "APIGroup_d3da",
       "publish_id" : "ca2631e233a74a758744ae1e19cc5ad7",
       "group_id" : "6acd94abe58747ee8a73b10c70817bac",
       "name" : "API_test",
       "remark" : "FunctionGraph backend API",
       "run_env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "id" : "11cbec3a7a8345ca981b86d161bc436e",
       "req_uri" : "/appcode"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:api_name. Please refer to the support documentation"
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
     "error_code" : "APIG.3004",
     "error_msg" : "App 356de8eb7a8742168586e5daf5339965 does not exist"
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
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
