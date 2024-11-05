:original_name: ShowPlugin.html

.. _ShowPlugin:

Querying Plug-in Details
========================

Function
--------

This API is used to query the details of a plug-in.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/plugins/{plugin_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | plugin_id   | Yes       | String | Plug-in ID.                                                                                             |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                 |
   +=======================+=======================+=============================================================================================================================+
   | plugin_id             | String                | Plug-in ID.                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_name           | String                | Plug-in name. Start with a letter, and include only letters, digits, hyphens (-), and underscores(_). (3 to 255 characters) |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_type           | String                | Plug-in type.                                                                                                               |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  cors: Cross-origin resource sharing.                                                                                     |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  set_resp_headers: HTTP response header management.                                                                       |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  kafka_log: Kafka log push.                                                                                               |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  breaker: Circuit breaker.                                                                                                |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  rate_limit: Request throttling.                                                                                          |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  third_auth: Third-party authentication.                                                                                  |
   |                       |                       |                                                                                                                             |
   |                       |                       | Enumeration values:                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **cors**                                                                                                                 |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **set_resp_headers**                                                                                                     |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **kafka_log**                                                                                                            |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **breaker**                                                                                                              |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **rate_limit**                                                                                                           |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **third_auth**                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_scope          | String                | Plug-in scope. global: Visible to all gateways.                                                                             |
   |                       |                       |                                                                                                                             |
   |                       |                       | Enumeration values:                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **global**                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_content        | String                | Plug-in content in JSON format. For details, see the model definition.                                                      |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  CorsPluginContent                                                                                                        |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  SetRespHeadersContent                                                                                                    |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  KafkaLogContent                                                                                                          |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  BreakerContent                                                                                                           |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  RateLimitContent                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  ThirdAuthContent                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | Maximum: **65535**                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | remark                | String                | Plug-in description, with a maximum of 255 characters.                                                                      |
   |                       |                       |                                                                                                                             |
   |                       |                       | Maximum: **255**                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time.                                                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

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
     "plugin_id" : "5b729aa252764739b3s237ef0d66dc63",
     "plugin_name" : "CORS",
     "plugin_type" : "cors",
     "plugin_scope" : "global",
     "plugin_content" : "{\"allow_origin\": \"*\",\"allow_methods\": \"GET,POST,PUT\",\"allow_headers\": \"Content-Type,Accept,Accept-Ranges,Cache-Control\",\"expose_headers\": \"X-Request-Id,X-Apig-Latency\",\"max_age\": 172800,\"allow_credentials\": true}",
     "remark" : "Cross-origin resource sharing",
     "create_time" : "2022-11-02T12:31:23.353Z",
     "update_time" : "2022-11-02T12:31:23.353Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:instance_id. Please refer to the support documentation"
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
     "error_code" : "APIG.3068",
     "error_msg" : "Plugin b294018ee0554156a875b3513e02e5b9 does not exist"
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
