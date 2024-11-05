:original_name: AttachApiToPlugin.html

.. _AttachApiToPlugin:

Binding a Plug-in to APIs
=========================

Function
--------

This API is used to bind a plug-in to APIs.

-  Plug-ins can be bound only to published APIs.

-  Plug-ins take effect immediately after binding.

-  Plug-ins take effect immediately after being modified.

-  An API can be bound with only one plug-in of the same type. Binding another plug-in will overwrite the previous one.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/plugins/{plugin_id}/attach

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+-----------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                   |
   +=================+=================+==================+===============================================+
   | env_id          | Yes             | String           | ID of the environment for binding to the API. |
   +-----------------+-----------------+------------------+-----------------------------------------------+
   | api_ids         | Yes             | Array of strings | IDs of bound APIs.                            |
   |                 |                 |                  |                                               |
   |                 |                 |                  | Array Length: **1 - 500**                     |
   +-----------------+-----------------+------------------+-----------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +------------------+-----------------------------------------------------------------------------------------------+-----------------+
   | Parameter        | Type                                                                                          | Description     |
   +==================+===============================================================================================+=================+
   | attached_plugins | Array of :ref:`PluginApiAttachInfo <attachapitoplugin__response_pluginapiattachinfo>` objects | Bound plug-ins. |
   +------------------+-----------------------------------------------------------------------------------------------+-----------------+

.. _attachapitoplugin__response_pluginapiattachinfo:

.. table:: **Table 5** PluginApiAttachInfo

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                 |
   +=======================+=======================+=============================================================================================================================+
   | plugin_attach_id      | String                | Plug-in binding record ID.                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
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
   | env_id                | String                | ID of the environment for binding to the API.                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | env_name              | String                | Name of the environment for binding to the API.                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | api_id                | String                | API ID.                                                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | api_name              | String                | API name.                                                                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | attached_time         | String                | Binding time.                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+

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

Binding an API with plug-ins

.. code-block::

   {
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
     "api_ids" : [ "8aa097b00e9843efabc9c593d11b769d" ]
   }

Example Responses
-----------------

**Status code: 201**

OK

.. code-block::

   {
     "attached_plugins" : [ {
       "plugin_attach_id" : "8aa097b00e9843efacb9c593d11b769e",
       "plugin_id" : "5b729aa252764739b3s237ef0d66dc63",
       "plugin_name" : "CORS",
       "plugin_type" : "cors",
       "plugin_scope" : "global",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "api_id" : "8aa097b00e9843efabc9c593d11b769d",
       "api_name" : "api_name",
       "attached_time" : "2022-11-02T12:31:23.353Z"
     } ]
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
201         OK
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
