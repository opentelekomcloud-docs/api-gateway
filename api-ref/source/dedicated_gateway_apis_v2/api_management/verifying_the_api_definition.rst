:original_name: CheckApisV2.html

.. _CheckApisV2:

Verifying the API Definition
============================

Function
--------

This API is used to verify the API definition, that is, whether the API path or name already exists.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/apis/check

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                          |
   +=================+=================+=================+======================================================================================+
   | name            | No              | String          | API name.                                                                            |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | This parameter is mandatory when type is set to name.                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | req_method      | No              | String          | Request method.                                                                      |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | This parameter is mandatory when type is set to path.                                |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                  |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **GET**                                                                           |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **POST**                                                                          |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **PUT**                                                                           |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **DELETE**                                                                        |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **HEAD**                                                                          |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **PATCH**                                                                         |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **OPTIONS**                                                                       |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **ANY**                                                                           |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | req_uri         | No              | String          | Access address of the API.                                                           |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | This parameter is mandatory when type is set to path.                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | match_mode      | No              | String          | API matching mode:                                                                   |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  SWA: Prefix match                                                                 |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  NORMAL: Exact match                                                               |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | This parameter is mandatory when type is set to path.                                |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                  |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **SWA**                                                                           |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **NORMAL**                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | group_id        | No              | String          | Group ID.                                                                            |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | This parameter is mandatory for checking for duplicate API definitions in the group. |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | roma_app_id     | No              | String          | Integration application ID.                                                          |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | This is not supported currently.                                                     |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | api_id          | No              | String          | ID of the API to be compared.                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+
   | type            | Yes             | String          | Verification type:                                                                   |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  path: path type                                                                   |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  name: name type                                                                   |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | Enumeration values:                                                                  |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **path**                                                                          |
   |                 |                 |                 |                                                                                      |
   |                 |                 |                 | -  **name**                                                                          |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

.. code-block::

   {
     "type" : "name",
     "name" : "api_demo"
   }

Example Responses
-----------------

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3202",
     "error_msg" : "The API name already exists, api_name:api_demo"
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
     "error_code" : "APIG.3030",
     "error_msg" : "The instance does not exist;id:f0fa1789-3b76-433b-a787-9892951c620ec"
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
204         No Content
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
