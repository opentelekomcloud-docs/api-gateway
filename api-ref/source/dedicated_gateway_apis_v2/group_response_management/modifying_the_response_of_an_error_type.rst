:original_name: UpdateGatewayResponseTypeV2.html

.. _UpdateGatewayResponseTypeV2:

Modifying the Response of an Error Type
=======================================

Function
--------

This API is used to modify the response of an error type defined for an API group.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/gateway-responses/{response_id}/{response_type}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`.                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | Gateway ID, which can be obtained from the gateway information on the APIG console.                                                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String          | API group ID.                                                                                                                                 |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | response_id     | Yes             | String          | Response ID.                                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | response_type   | Yes             | String          | Error type. Options:                                                                                                                          |
   |                 |                 |                 |                                                                                                                                               |
   |                 |                 |                 | -  AUTH_FAILURE: IAM or app authentication failed.                                                                                            |
   |                 |                 |                 | -  AUTH_HEADER_MISSING: The identity source is missing.                                                                                       |
   |                 |                 |                 | -  AUTHORIZER_FAILURE: Custom authentication failed.                                                                                          |
   |                 |                 |                 | -  AUTHORIZER_CONF_FAILURE: A custom authorizer error has occurred. For example, communication failed or an error response was returned.      |
   |                 |                 |                 | -  AUTHORIZER_IDENTITIES_FAILURE: The identity source of the frontend custom authorizer is missing or invalid.                                |
   |                 |                 |                 | -  BACKEND_UNAVAILABLE: The backend is unavailable due to communication error.                                                                |
   |                 |                 |                 | -  BACKEND_TIMEOUT: Communication with the backend timed out.                                                                                 |
   |                 |                 |                 | -  THROTTLED: The request was rejected due to throttling.                                                                                     |
   |                 |                 |                 | -  UNAUTHORIZED: The credential you use is not authorized to call the API.                                                                    |
   |                 |                 |                 | -  ACCESS_DENIED: Access denied. For example, the access control policy is triggered or an attack is detected.                                |
   |                 |                 |                 | -  NOT_FOUND: No API is matched.                                                                                                              |
   |                 |                 |                 | -  REQUEST_PARAMETERS_FAILURE: Invalid request parameter or unsupported HTTP method.                                                          |
   |                 |                 |                 | -  DEFAULT_4XX: Another 4XX error occurred.                                                                                                   |
   |                 |                 |                 | -  DEFAULT_5XX: Another 5XX error occurred.                                                                                                   |
   |                 |                 |                 | -  THIRD_AUTH_FAILURE: Third-party authentication failed.                                                                                     |
   |                 |                 |                 | -  THIRD_AUTH_IDENTITIES_FAILURE: The identity source of the third-party authorizer is missing or invalid.                                    |
   |                 |                 |                 | -  THIRD_AUTH_CONF_FAILURE: A third-party authorizer error has occurred. For example, communication failed or an error response was returned. |
   |                 |                 |                 | -  ORCHESTRATION_PARAMETER_NOT_FOUND: Parameter orchestration failed. No input parameter is found in the request.                             |
   |                 |                 |                 | -  ORCHESTRATION_FAILURE: Parameter orchestration failed. No orchestration rule to match.                                                     |
   |                 |                 |                 |                                                                                                                                               |
   |                 |                 |                 | Enumeration values:                                                                                                                           |
   |                 |                 |                 |                                                                                                                                               |
   |                 |                 |                 | -  **AUTH_FAILURE**                                                                                                                           |
   |                 |                 |                 | -  **AUTH_HEADER_MISSING**                                                                                                                    |
   |                 |                 |                 | -  **AUTHORIZER_FAILURE**                                                                                                                     |
   |                 |                 |                 | -  **AUTHORIZER_CONF_FAILURE**                                                                                                                |
   |                 |                 |                 | -  **AUTHORIZER_IDENTITIES_FAILURE**                                                                                                          |
   |                 |                 |                 | -  **BACKEND_UNAVAILABLE**                                                                                                                    |
   |                 |                 |                 | -  **BACKEND_TIMEOUT**                                                                                                                        |
   |                 |                 |                 | -  **THROTTLED**                                                                                                                              |
   |                 |                 |                 | -  **UNAUTHORIZED**                                                                                                                           |
   |                 |                 |                 | -  **ACCESS_DENIED**                                                                                                                          |
   |                 |                 |                 | -  **NOT_FOUND**                                                                                                                              |
   |                 |                 |                 | -  **REQUEST_PARAMETERS_FAILURE**                                                                                                             |
   |                 |                 |                 | -  **DEFAULT_4XX**                                                                                                                            |
   |                 |                 |                 | -  **DEFAULT_5XX**                                                                                                                            |
   |                 |                 |                 | -  **THIRD_AUTH_FAILURE**                                                                                                                     |
   |                 |                 |                 | -  **THIRD_AUTH_IDENTITIES_FAILURE**                                                                                                          |
   |                 |                 |                 | -  **THIRD_AUTH_CONF_FAILURE**                                                                                                                |
   |                 |                 |                 | -  **ORCHESTRATION_PARAMETER_NOT_FOUND**                                                                                                      |
   |                 |                 |                 | -  **ORCHESTRATION_FAILURE**                                                                                                                  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                                 | Description                                                                            |
   +=================+=================+======================================================================================================+========================================================================================+
   | status          | No              | Integer                                                                                              | HTTP status code of the response. The value ranges from 200 to 599, but cannot be 444. |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | body            | No              | String                                                                                               | Response body template.                                                                |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | headers         | No              | Array of :ref:`ResponseInfoHeader <updategatewayresponsetypev2__request_responseinfoheader>` objects | Custom response header.                                                                |
   |                 |                 |                                                                                                      |                                                                                        |
   |                 |                 |                                                                                                      | Array Length: **0 - 10**                                                               |
   +-----------------+-----------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+

.. _updategatewayresponsetypev2__request_responseinfoheader:

.. table:: **Table 4** ResponseInfoHeader

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

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +--------------------+------------------------------------------------------------------------------------------------+-------------+
   | Parameter          | Type                                                                                           | Description |
   +====================+================================================================================================+=============+
   | {User defined key} | Map<String,\ :ref:`ResponseInfoResp <updategatewayresponsetypev2__response_responseinforesp>`> | OK          |
   +--------------------+------------------------------------------------------------------------------------------------+-------------+

.. _updategatewayresponsetypev2__response_responseinforesp:

.. table:: **Table 6** ResponseInfoResp

   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                  | Description                                                                            |
   +=======================+=======================================================================================================+========================================================================================+
   | status                | Integer                                                                                               | HTTP status code of the response. The value ranges from 200 to 599, but cannot be 444. |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | body                  | String                                                                                                | Response body template.                                                                |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | headers               | Array of :ref:`ResponseInfoHeader <updategatewayresponsetypev2__response_responseinfoheader>` objects | Custom response header.                                                                |
   |                       |                                                                                                       |                                                                                        |
   |                       |                                                                                                       | Array Length: **0 - 10**                                                               |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+
   | default               | Boolean                                                                                               | Indicates whether the response is the default response.                                |
   +-----------------------+-------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------+

.. _updategatewayresponsetypev2__response_responseinfoheader:

.. table:: **Table 7** ResponseInfoHeader

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

**Status code: 404**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 12** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Modifying the response of an error type defined for an API group

.. code-block::

   {
     "body" : "body: \"{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}\"",
     "status" : 403
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "ACCESS_DENIED" : {
       "body" : "{\"error_code\":\"$context.error.code\",\"error_msg\":\"$context.error.message\",\"request_id\":\"$context.requestId\"}",
       "default" : true,
       "status" : 403
     }
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:group_id. Please refer to the support documentation"
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
