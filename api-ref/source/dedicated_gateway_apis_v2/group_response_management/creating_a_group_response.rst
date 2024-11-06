:original_name: CreateGatewayResponseV2.html

.. _CreateGatewayResponseV2:

Creating a Group Response
=========================

Function
--------

This API is used to create a response for an API group.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/gateway-responses

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | group_id    | Yes       | String | API group ID.                                                                                           |
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

   +-----------------+-----------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                              | Description                                                                                                                             |
   +=================+=================+===================================================================================+=========================================================================================================================================+
   | name            | Yes             | String                                                                            | Response name. Enter 1 to 64 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed.                            |
   +-----------------+-----------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | responses       | No              | Map<String,\ :ref:`ResponseInfo <creategatewayresponsev2__request_responseinfo>`> | Response type definition. key indicates the error type. Options of key:                                                                 |
   |                 |                 |                                                                                   |                                                                                                                                         |
   |                 |                 |                                                                                   | -  AUTH_FAILURE: Authentication failed.                                                                                                 |
   |                 |                 |                                                                                   | -  AUTH_HEADER_MISSING: The identity source is missing.                                                                                 |
   |                 |                 |                                                                                   | -  AUTHORIZER_FAILURE: Custom authentication failed.                                                                                    |
   |                 |                 |                                                                                   | -  AUTHORIZER_CONF_FAILURE: Custom authorizer error.                                                                                    |
   |                 |                 |                                                                                   | -  AUTHORIZER_IDENTITIES_FAILURE: The identity source of the custom authorizer is invalid.                                              |
   |                 |                 |                                                                                   | -  BACKEND_UNAVAILABLE: The backend is unavailable.                                                                                     |
   |                 |                 |                                                                                   | -  BACKEND_TIMEOUT: Backend timed out.                                                                                                  |
   |                 |                 |                                                                                   | -  THROTTLED: The request was rejected due to request throttling.                                                                       |
   |                 |                 |                                                                                   | -  UNAUTHORIZED: The app you are using has not been authorized to call the API.                                                         |
   |                 |                 |                                                                                   | -  ACCESS_DENIED: Access denied.                                                                                                        |
   |                 |                 |                                                                                   | -  NOT_FOUND: No API is found.                                                                                                          |
   |                 |                 |                                                                                   | -  REQUEST_PARAMETERS_FAILURE: Invalid request parameter.                                                                               |
   |                 |                 |                                                                                   | -  DEFAULT_4XX: Default 4XX error occurred.                                                                                             |
   |                 |                 |                                                                                   | -  DEFAULT_5XX: Default 5XX error occurred.                                                                                             |
   |                 |                 |                                                                                   | -  THIRD_AUTH_FAILURE: Third-party authentication failed.                                                                               |
   |                 |                 |                                                                                   | -  THIRD_AUTH_IDENTITIES_FAILURE: Identity source of the third-party authorizer is invalid.                                             |
   |                 |                 |                                                                                   | -  THIRD_AUTH_CONF_FAILURE: Third-party authorizer configuration error.                                                                 |
   |                 |                 |                                                                                   | -  ORCHESTRATION_PARAMETER_NOT_FOUND: No parameters are input to match the parameter orchestration rule, causing orchestration failure. |
   |                 |                 |                                                                                   | -  ORCHESTRATION_FAILURE: Input parameters cannot match orchestration rules, causing orchestration failure.                             |
   |                 |                 |                                                                                   |                                                                                                                                         |
   |                 |                 |                                                                                   | Each error type is in JSON format.                                                                                                      |
   +-----------------+-----------------+-----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _creategatewayresponsev2__request_responseinfo:

.. table:: **Table 4** ResponseInfo

   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                             | Description                                                                            |
   +=================+=================+==================================================================================================+========================================================================================+
   | status          | No              | Integer                                                                                          | HTTP status code of the response. The value ranges from 200 to 599, but cannot be 444. |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | body            | No              | String                                                                                           | Response body template.                                                                |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | headers         | No              | Array of :ref:`ResponseInfoHeader <creategatewayresponsev2__request_responseinfoheader>` objects | Custom response header.                                                                |
   |                 |                 |                                                                                                  |                                                                                        |
   |                 |                 |                                                                                                  | Array Length: **0 - 10**                                                               |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+

.. _creategatewayresponsev2__request_responseinfoheader:

.. table:: **Table 5** ResponseInfoHeader

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                         |
   +=================+=================+=================+=====================================================================================================================+
   | key             | No              | String          | Key of the custom group response header, which can contain 1 to 128 characters of letters, digits, and hyphens (-). |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value of the custom group response header, which is a string of 1 to 1,024 characters.                              |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Minimum: **1**                                                                                                      |
   |                 |                 |                 |                                                                                                                     |
   |                 |                 |                 | Maximum: **1024**                                                                                                   |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 6** Response body parameters

   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                       | Description                                                                                                                             |
   +=======================+============================================================================================+=========================================================================================================================================+
   | name                  | String                                                                                     | Response name.                                                                                                                          |
   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | responses             | Map<String,\ :ref:`ResponseInfoResp <creategatewayresponsev2__response_responseinforesp>`> | Response type definition. key indicates the error type. Options of key:                                                                 |
   |                       |                                                                                            |                                                                                                                                         |
   |                       |                                                                                            | -  AUTH_FAILURE: Authentication failed.                                                                                                 |
   |                       |                                                                                            | -  AUTH_HEADER_MISSING: The identity source is missing.                                                                                 |
   |                       |                                                                                            | -  AUTHORIZER_FAILURE: Custom authentication failed.                                                                                    |
   |                       |                                                                                            | -  AUTHORIZER_CONF_FAILURE: Custom authorizer error.                                                                                    |
   |                       |                                                                                            | -  AUTHORIZER_IDENTITIES_FAILURE: The identity source of the custom authorizer is invalid.                                              |
   |                       |                                                                                            | -  BACKEND_UNAVAILABLE: The backend is unavailable.                                                                                     |
   |                       |                                                                                            | -  BACKEND_TIMEOUT: Backend timed out.                                                                                                  |
   |                       |                                                                                            | -  THROTTLED: The request was rejected due to request throttling.                                                                       |
   |                       |                                                                                            | -  UNAUTHORIZED: The app you are using has not been authorized to call the API.                                                         |
   |                       |                                                                                            | -  ACCESS_DENIED: Access denied.                                                                                                        |
   |                       |                                                                                            | -  NOT_FOUND: No API is found.                                                                                                          |
   |                       |                                                                                            | -  REQUEST_PARAMETERS_FAILURE: Invalid request parameter.                                                                               |
   |                       |                                                                                            | -  DEFAULT_4XX: Default 4XX error occurred.                                                                                             |
   |                       |                                                                                            | -  DEFAULT_5XX: Default 5XX error occurred.                                                                                             |
   |                       |                                                                                            | -  THIRD_AUTH_FAILURE: Third-party authentication failed.                                                                               |
   |                       |                                                                                            | -  THIRD_AUTH_IDENTITIES_FAILURE: Identity source of the third-party authorizer is invalid.                                             |
   |                       |                                                                                            | -  THIRD_AUTH_CONF_FAILURE: Third-party authorizer configuration error.                                                                 |
   |                       |                                                                                            | -  ORCHESTRATION_PARAMETER_NOT_FOUND: No parameters are input to match the parameter orchestration rule, causing orchestration failure. |
   |                       |                                                                                            | -  ORCHESTRATION_FAILURE: Input parameters cannot match orchestration rules, causing orchestration failure.                             |
   |                       |                                                                                            |                                                                                                                                         |
   |                       |                                                                                            | Each error type is in JSON format.                                                                                                      |
   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                                                                                     | Response ID.                                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | default               | Boolean                                                                                    | Indicates whether the group response is the default response.                                                                           |
   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                                                                                     | Creation time.                                                                                                                          |
   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                                                                                     | Update time.                                                                                                                            |
   +-----------------------+--------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

.. _creategatewayresponsev2__response_responseinforesp:

.. table:: **Table 7** ResponseInfoResp

   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                              | Description                                                                            |
   +=======================+===================================================================================================+========================================================================================+
   | status                | Integer                                                                                           | HTTP status code of the response. The value ranges from 200 to 599, but cannot be 444. |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | body                  | String                                                                                            | Response body template.                                                                |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | headers               | Array of :ref:`ResponseInfoHeader <creategatewayresponsev2__response_responseinfoheader>` objects | Custom response header.                                                                |
   |                       |                                                                                                   |                                                                                        |
   |                       |                                                                                                   | Array Length: **0 - 10**                                                               |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | default               | Boolean                                                                                           | Indicates whether the response is the default response.                                |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+

.. _creategatewayresponsev2__response_responseinfoheader:

.. table:: **Table 8** ResponseInfoHeader

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                         |
   +=======================+=======================+=====================================================================================================================+
   | key                   | String                | Key of the custom group response header, which can contain 1 to 128 characters of letters, digits, and hyphens (-). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Value of the custom group response header, which is a string of 1 to 1,024 characters.                              |
   |                       |                       |                                                                                                                     |
   |                       |                       | Minimum: **1**                                                                                                      |
   |                       |                       |                                                                                                                     |
   |                       |                       | Maximum: **1024**                                                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 12** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 13** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Creating a response for an API group

.. code-block::

   {
     "name" : "response_demo"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "create_time" : "2020-08-12T14:52:02.829753306+08:00",
     "update_time" : "2020-08-12T14:52:02.829753306+08:00",
     "default" : false,
     "id" : "e839b367e10f4ab19d1c5008e476b83a",
     "name" : "response_demo",
     "responses" : {
       "ACCESS_DENIED" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 403
       },
       "AUTHORIZER_CONF_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 500
       },
       "AUTHORIZER_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 500
       },
       "AUTHORIZER_IDENTITIES_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 401
       },
       "AUTH_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 401
       },
       "AUTH_HEADER_MISSING" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 401
       },
       "BACKEND_TIMEOUT" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 504
       },
       "BACKEND_UNAVAILABLE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 502
       },
       "DEFAULT_4XX" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true
       },
       "DEFAULT_5XX" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true
       },
       "NOT_FOUND" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 404
       },
       "REQUEST_PARAMETERS_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 400
       },
       "THROTTLED" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 429
       },
       "UNAUTHORIZED" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 401
       },
       "THIRD_AUTH_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 401
       },
       "THIRD_AUTH_IDENTITIES_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 401
       },
       "THIRD_AUTH_CONF_FAILURE" : {
         "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
         "default" : true,
         "status" : 500
       }
     }
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:name. Please refer to the support documentation"
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
     "error_code" : "APIG.3001",
     "error_msg" : "API group c77f5e81d9cb4424bf704ef2b0ac7600 does not exist"
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
