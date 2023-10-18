:original_name: DebugApiV2.html

.. _DebugApiV2:

Debugging an API
================

Function
--------

This API is used to debug an API in a specified environment. The API caller must have the permissions required for accessing this API.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/apis/debug/{api_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | api_id      | Yes       | String | API ID.                                                                                                               |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                      | Description                                                                                                                                                                                 |
   +=================+=================+===========================+=============================================================================================================================================================================================+
   | body            | No              | String                    | Message body, with a maximum of 2,097,152 bytes.                                                                                                                                            |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | header          | No              | Map<String,Array<String>> | Header parameters, with each value being a character string array. Each parameter name must meet the following requirements:                                                                |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Contains letters, digits, periods (.), or hyphens (-).                                                                                                                                   |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Starts with a letter, with a maximum of 32 bytes.                                                                                                                                        |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Case-insensitive and cannot start with X-Apig- or X-Sdk-.                                                                                                                                |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Case-insensitive and cannot be X-Stage.                                                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Case-insensitive and cannot be X-Auth-Token or Authorization when mode is set to MARKET or CONSUMER.                                                                                     |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | .. note::                                                                                                                                                                                   |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           |    Each header name is normalized before use. For example, x-MY-hEaDer is normalized as X-My-Header.                                                                                        |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | method          | Yes             | String                    | API request method.                                                                                                                                                                         |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | Enumeration values:                                                                                                                                                                         |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **GET**                                                                                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **POST**                                                                                                                                                                                 |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **PUT**                                                                                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **DELETE**                                                                                                                                                                               |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **HEAD**                                                                                                                                                                                 |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **PATCH**                                                                                                                                                                                |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  **OPTIONS**                                                                                                                                                                              |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mode            | Yes             | String                    | Debugging mode:                                                                                                                                                                             |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  DEVELOPER: Debug the definitions of an API that has not been published.                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  CONSUMER: Debug the definitions of an API that has been published in a specified environment.                                                                                            |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | .. note::                                                                                                                                                                                   |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           |    In DEVELOPER mode, the API caller must be the API provider.                                                                                                                              |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | In CONSUMER mode, the API caller must be the API provider or has been authorized to access the API in a specific environment.                                                               |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | path            | Yes             | String                    | Request path of the API, starting with a slash (/) and containing up to 1024 characters.                                                                                                    |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | .. note::                                                                                                                                                                                   |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           |    The request path must meet the requirements so that it can be correctly decoded after percent-encoding.                                                                                  |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query           | No              | Map<String,Array<String>> | Query strings, with each value being a character string array. Each parameter name must meet the following requirements:                                                                    |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Contains letters, digits, periods (.), hyphens (-), or underscores (_).                                                                                                                  |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Starts with a letter, with a maximum of 32 bytes.                                                                                                                                        |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Case-insensitive and cannot start with X-Apig- or X-Sdk-.                                                                                                                                |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  Case-insensitive and cannot be X-Stage.                                                                                                                                                  |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheme          | Yes             | String                    | Request protocol.                                                                                                                                                                           |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  HTTP                                                                                                                                                                                     |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  HTTPS                                                                                                                                                                                    |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_key         | No              | String                    | AppKey used in the debugging request.                                                                                                                                                       |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_secret      | No              | String                    | AppSecret used in the debugging request.                                                                                                                                                    |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain          | No              | String                    | Access domain name of the API. If no value is specified, one of the following default values will be used based on the mode:                                                                |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  DEVELOPER: The subdomain name of the API group will be used.                                                                                                                             |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  MARKET: This parameter is not used currently.                                                                                                                                            |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  CONSUMER: The subdomain name of the API group will be used.                                                                                                                              |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | stage           | No              | String                    | Running environment specified by the debugging request. This parameter is valid only when mode is set to CONSUMER. If this parameter is not specified, the following default value is used: |
   |                 |                 |                           |                                                                                                                                                                                             |
   |                 |                 |                           | -  CONSUMER RELEASE                                                                                                                                                                         |
   +-----------------+-----------------+---------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                             |
   +=======================+=======================+=========================================================================================================================+
   | request               | String                | Body of the debugging request.                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | response              | String                | Body of the debugging response, with a maximum of 2,097,152 bytes. Any content beyond this threshold will be truncated. |
   |                       |                       |                                                                                                                         |
   |                       |                       | .. note::                                                                                                               |
   |                       |                       |                                                                                                                         |
   |                       |                       |    Any content beyond the length limit will be truncated, and text [TRUNCATED] will be added to the response body.      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | latency               | Integer               | Debugging duration in milliseconds.                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+
   | log                   | String                | Debugging logs.                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------+

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

.. code-block::

   {
     "mode" : "DEVELOPER",
     "scheme" : "HTTPS",
     "method" : "GET",
     "path" : "/test/mock"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "request" : "GET /test/mock HTTP/1.1\r\nHost: c77f5e81d9cb4424bf704ef2b0ac7600.apic.****.com\r\nUser-Agent: APIGatewayDebugClient/1.0\r\nX-Apig-Mode: debug\r\n\r\n",
     "response" : "HTTP/1.1 200 OK\r\nTransfer-Encoding: chunked\r\nConnection: keep-alive\r\nContent-Type: application/json\r\nDate: Mon, 03 Aug 2020 02:51:22 GMT\r\nServer: api-gateway\r\nX-Apig-Latency: 0\r\nX-Apig-Ratelimit-Api: remain:99,limit:100,time:1 minute\r\nX-Apig-Ratelimit-Api-Allenv: remain:14999,limit:15000,time:1 second\r\nX-Request-Id: d4ec6e33148bdeffe8f55b43472d1251\r\n\r\nmock success",
     "latency" : 5,
     "log" : ""
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:mode. Please refer to the support documentation"
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
     "error_msg" : "API 3a955b791bd24b1c9cd94c745f8d1aad does not exist"
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
