:original_name: ExportApiDefinitionsV2.html

.. _ExportApiDefinitionsV2:

Exporting APIs
==============

Function
--------

This API is used to export APIs in a specified API group. The content of the exported file complies with the Swagger standard. For details about the custom extended fields of APIG, see section "Extended Definition" in the User Guide.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/openapi/export

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+---------------------+
   | Parameter       | Mandatory       | Type            | Description         |
   +=================+=================+=================+=====================+
   | oas_version     | No              | String          | Open API version.   |
   |                 |                 |                 |                     |
   |                 |                 |                 | Default: **2.0**    |
   |                 |                 |                 |                     |
   |                 |                 |                 | Enumeration values: |
   |                 |                 |                 |                     |
   |                 |                 |                 | -  **2.0**          |
   |                 |                 |                 | -  **3.0**          |
   +-----------------+-----------------+-----------------+---------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                           |
   +=================+=================+==================+=======================================================================================================================================================================+
   | env_id          | Yes             | String           | ID of the environment in which APIs of a group have been published.                                                                                                   |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String           | API group ID.                                                                                                                                                         |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | define          | No              | String           | Definition scope of the APIs to be exported:                                                                                                                          |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | -  spec: basic definitions, including only the frontend definitions.                                                                                                  |
   |                 |                 |                  | -  proxy: full definitions, including the frontend and backend definitions.                                                                                           |
   |                 |                 |                  | -  all: extended definitions, including the frontend and backend definitions as well as request throttling policies, access control policies, and custom authorizers. |
   |                 |                 |                  | -  dev: development definitions, including the frontend and backend definitions of APIs that have not been published.                                                 |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | Default: **spec**                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | Enumeration values:                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | -  **spec**                                                                                                                                                           |
   |                 |                 |                  | -  **proxy**                                                                                                                                                          |
   |                 |                 |                  | -  **all**                                                                                                                                                            |
   |                 |                 |                  | -  **dev**                                                                                                                                                            |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String           | Format for exporting API definitions.                                                                                                                                 |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | Default: **json**                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | Enumeration values:                                                                                                                                                   |
   |                 |                 |                  |                                                                                                                                                                       |
   |                 |                 |                  | -  **json**                                                                                                                                                           |
   |                 |                 |                  | -  **yaml**                                                                                                                                                           |
   |                 |                 |                  | -  **yml**                                                                                                                                                            |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | version         | No              | String           | Version number of the APIs after exporting. The default value is the current date and time.                                                                           |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | apis            | No              | Array of strings | IDs of the APIs to be exported.                                                                                                                                       |
   +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   ========= ==== ===========
   Parameter Type Description
   ========= ==== ===========
   ``-``     File OK
   ========= ==== ===========

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

Exporting APIs

.. code-block::

   {
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
     "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
     "define" : "all"
   }

Example Responses
-----------------

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2001",
     "error_msg" : "The request parameters must be specified,parameterName:env_id. Please refer to the support documentation"
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
