:original_name: UpdateGatewayResponseTypeV2.html

.. _UpdateGatewayResponseTypeV2:

Modifying the Response of an Error Type
=======================================

Function
--------

This API is used to modify the response of an error type defined for an API group.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/gateway-responses/{response_id}/{response_type}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                           |
   +=================+=================+=================+=======================================================================================================================+
   | project_id      | Yes             | String          | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id     | Yes             | String          | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String          | API group ID.                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | response_id     | Yes             | String          | Response ID.                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+
   | response_type   | Yes             | String          | Error type.                                                                                                           |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | Enumeration values:                                                                                                   |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **AUTH_FAILURE**                                                                                                   |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **AUTH_HEADER_MISSING**                                                                                            |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **AUTHORIZER_FAILURE**                                                                                             |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **AUTHORIZER_CONF_FAILURE**                                                                                        |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **AUTHORIZER_IDENTITIES_FAILURE**                                                                                  |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **BACKEND_UNAVAILABLE**                                                                                            |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **BACKEND_TIMEOUT**                                                                                                |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **THROTTLED**                                                                                                      |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **UNAUTHORIZED**                                                                                                   |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **ACCESS_DENIED**                                                                                                  |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **NOT_FOUND**                                                                                                      |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **REQUEST_PARAMETERS_FAILURE**                                                                                     |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **DEFAULT_4XX**                                                                                                    |
   |                 |                 |                 |                                                                                                                       |
   |                 |                 |                 | -  **DEFAULT_5XX**                                                                                                    |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ========= ========= ======= =================================
   Parameter Mandatory Type    Description
   ========= ========= ======= =================================
   status    No        Integer HTTP status code of the response.
   body      No        String  Response body template.
   ========= ========= ======= =================================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------------+------------------------------------------------------------------------------------------------+-------------+
   | Parameter          | Type                                                                                           | Description |
   +====================+================================================================================================+=============+
   | {User defined key} | Map<String,\ :ref:`ResponseInfoResp <updategatewayresponsetypev2__response_responseinforesp>`> | OK          |
   +--------------------+------------------------------------------------------------------------------------------------+-------------+

.. _updategatewayresponsetypev2__response_responseinforesp:

.. table:: **Table 5** ResponseInfoResp

   +-----------+---------+---------------------------------------------------------+
   | Parameter | Type    | Description                                             |
   +===========+=========+=========================================================+
   | status    | Integer | HTTP status code of the response.                       |
   +-----------+---------+---------------------------------------------------------+
   | body      | String  | Response body template.                                 |
   +-----------+---------+---------------------------------------------------------+
   | default   | Boolean | Indicates whether the response is the default response. |
   +-----------+---------+---------------------------------------------------------+

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
