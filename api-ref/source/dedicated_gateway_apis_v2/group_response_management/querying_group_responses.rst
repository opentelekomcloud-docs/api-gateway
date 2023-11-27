:original_name: ListGatewayResponsesV2_1.html

.. _ListGatewayResponsesV2_1:

Querying Group Responses
========================

Function
--------

This API is used to query the responses of an API group.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/gateway-responses

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

   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                     | Description                                          |
   +===========+==========================================================================================+======================================================+
   | size      | Integer                                                                                  | Length of the returned resource list.                |
   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                     | Number of resources that match the query conditions. |
   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+
   | responses | Array of :ref:`ResponsesInfo <listgatewayresponsesv2_1__response_responsesinfo>` objects | Response list.                                       |
   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listgatewayresponsesv2_1__response_responsesinfo:

.. table:: **Table 5** ResponsesInfo

   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                        | Description                                                                                |
   +=======================+=============================================================================================+============================================================================================+
   | name                  | String                                                                                      | Response name.                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | responses             | Map<String,\ :ref:`ResponseInfoResp <listgatewayresponsesv2_1__response_responseinforesp>`> | Response type definition. key indicates the error type. Options of key:                    |
   |                       |                                                                                             |                                                                                            |
   |                       |                                                                                             | -  AUTH_FAILURE: Authentication failed.                                                    |
   |                       |                                                                                             | -  AUTH_HEADER_MISSING: The identity source is missing.                                    |
   |                       |                                                                                             | -  AUTHORIZER_FAILURE: Custom authentication failed.                                       |
   |                       |                                                                                             | -  AUTHORIZER_CONF_FAILURE: Custom authorizer error.                                       |
   |                       |                                                                                             | -  AUTHORIZER_IDENTITIES_FAILURE: The identity source of the custom authorizer is invalid. |
   |                       |                                                                                             | -  BACKEND_UNAVAILABLE: The backend is unavailable.                                        |
   |                       |                                                                                             | -  BACKEND_TIMEOUT: Backend timed out.                                                     |
   |                       |                                                                                             | -  THROTTLED: The request was rejected due to request throttling.                          |
   |                       |                                                                                             | -  UNAUTHORIZED: The app you are using has not been authorized to call the API.            |
   |                       |                                                                                             | -  ACCESS_DENIED: Access denied.                                                           |
   |                       |                                                                                             | -  NOT_FOUND: No API is found.                                                             |
   |                       |                                                                                             | -  REQUEST_PARAMETERS_FAILURE: Invalid request parameter.                                  |
   |                       |                                                                                             | -  DEFAULT_4XX: Default 4XX error occurred.                                                |
   |                       |                                                                                             | -  DEFAULT_5XX: Default 5XX error occurred.                                                |
   |                       |                                                                                             |                                                                                            |
   |                       |                                                                                             | Each error type is in JSON format.                                                         |
   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | id                    | String                                                                                      | Response ID.                                                                               |
   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | default               | Boolean                                                                                     | Indicates whether the group response is the default response.                              |
   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | create_time           | String                                                                                      | Creation time.                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+
   | update_time           | String                                                                                      | Update time.                                                                               |
   +-----------------------+---------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------+

.. _listgatewayresponsesv2_1__response_responseinforesp:

.. table:: **Table 6** ResponseInfoResp

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

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 2,
     "size" : 2,
     "responses" : [ {
       "create_time" : "2020-08-12T06:52:02Z",
       "default" : false,
       "id" : "e839b367e10f4ab19d1c5008e476b83a",
       "name" : "response_demo",
       "update_time" : "2020-08-12T06:52:02Z"
     }, {
       "create_time" : "2020-07-31T11:39:23Z",
       "default" : true,
       "id" : "ed8e8c52ab0e4a1c9c809268e5002e64",
       "name" : "default",
       "update_time" : "2020-07-31T11:39:23Z"
     } ]
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
