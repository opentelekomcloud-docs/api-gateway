:original_name: ImportApiDefinitionsV2.html

.. _ImportApiDefinitionsV2:

Importing APIs
==============

Function
--------

This API is used to import APIs. The content of the imported file must comply with the Swagger standard. For details about the custom extended fields of APIG, see section "Extended Definition" in the User Guide.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/openapi/import

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

.. table:: **Table 3** FormData parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                   |
   +=================+=================+=================+===============================================================================+
   | is_create_group | No              | Boolean         | Specifies whether to create an API group.                                     |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Default: **true**                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | group_id        | No              | String          | API group ID. This parameter is required if is_create_group is set to false.  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | extend_mode     | No              | String          | Import mode of extended information.                                          |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | -  merge: Retain the original extended information if a conflict occurs.      |
   |                 |                 |                 | -  override: Override the original extended information if a conflict occurs. |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Default: **merge**                                                            |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Enumeration values:                                                           |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | -  **merge**                                                                  |
   |                 |                 |                 | -  **override**                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | simple_mode     | No              | Boolean         | Specifies whether to enable fast import.                                      |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Default: **false**                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | mock_mode       | No              | Boolean         | Specifies whether to enable the Mock backend.                                 |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Default: **false**                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | api_mode        | No              | String          | Import mode.                                                                  |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | -  merge: Retain the original API information if a conflict occurs.           |
   |                 |                 |                 | -  override: Override the original API information if a conflict occurs.      |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Default: **merge**                                                            |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Enumeration values:                                                           |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | -  **merge**                                                                  |
   |                 |                 |                 | -  **override**                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | file_name       | Yes             | File            | Request body in JSON or YAML format for importing APIs.                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------+
   | Parameter             | Type                                                                       | Description                                 |
   +=======================+============================================================================+=============================================+
   | success               | Array of :ref:`Success <importapidefinitionsv2__response_success>` objects | Import success information.                 |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------+
   | failure               | Array of :ref:`Failure <importapidefinitionsv2__response_failure>` objects | Import failure information.                 |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------+
   | swagger               | :ref:`Swagger <importapidefinitionsv2__response_swagger>` object           | Swagger file import result.                 |
   |                       |                                                                            |                                             |
   |                       |                                                                            | Currently, this parameter is not supported. |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------+
   | group_id              | String                                                                     | API group ID.                               |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------+
   | ignore                | Array of :ref:`Ignore <importapidefinitionsv2__response_ignore>` objects   | APIs that are not imported.                 |
   +-----------------------+----------------------------------------------------------------------------+---------------------------------------------+

.. _importapidefinitionsv2__response_success:

.. table:: **Table 5** Success

   +-----------------------+-----------------------+------------------------------------------------------+
   | Parameter             | Type                  | Description                                          |
   +=======================+=======================+======================================================+
   | path                  | String                | API request path.                                    |
   +-----------------------+-----------------------+------------------------------------------------------+
   | method                | String                | API request method.                                  |
   +-----------------------+-----------------------+------------------------------------------------------+
   | action                | String                | Import type. Options:                                |
   |                       |                       |                                                      |
   |                       |                       | -  update: Update the APIs to an existing API group. |
   |                       |                       | -  create: Create APIs for a new API group.          |
   |                       |                       |                                                      |
   |                       |                       | Enumeration values:                                  |
   |                       |                       |                                                      |
   |                       |                       | -  **update**                                        |
   |                       |                       | -  **create**                                        |
   +-----------------------+-----------------------+------------------------------------------------------+
   | id                    | String                | ID of a successfully imported API.                   |
   +-----------------------+-----------------------+------------------------------------------------------+

.. _importapidefinitionsv2__response_failure:

.. table:: **Table 6** Failure

   ========== ====== ==============================================
   Parameter  Type   Description
   ========== ====== ==============================================
   path       String API request path.
   error_msg  String Error message displayed for an import failure.
   method     String API request method.
   error_code String Error code displayed for an import failure.
   ========== ====== ==============================================

.. _importapidefinitionsv2__response_swagger:

.. table:: **Table 7** Swagger

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   id        String Swagger file No.
   result    String Import result description.
   ========= ====== ==========================

.. _importapidefinitionsv2__response_ignore:

.. table:: **Table 8** Ignore

   ========= ====== ===================
   Parameter Type   Description
   ========= ====== ===================
   method    String API request method.
   path      String API request path.
   ========= ====== ===================

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

Importing APIs

.. code-block::

   {
     "is_create_group" : false,
     "group_id" : "d9ce8c9eede54b3f841ec324fe0bfdc2",
     "file_name" : "APIGroup_test.json"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "group_id" : "d9ce8c9eede54b3f841ec324fe0bfdc2",
     "failure" : [ {
       "path" : "/test/demo",
       "error_msg" : "The API already exists, An API with the same combination of the method, path, and x-apigateway-match-mode fields already exists. API name: API_demo",
       "method" : "GET",
       "error_code" : "APIG.3301"
     } ],
     "success" : [ {
       "path" : "/test",
       "method" : "GET",
       "action" : "create",
       "id" : "8ae6bcafab6f49d78242bff26ad8a4f0"
     } ],
     "swagger" : {
       "id" : "e2ea8a7c1cfc49b3830437cb79d7fd59",
       "result" : "Success"
     }
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3201",
     "error_msg" : "The API group name already exists"
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
     "error_msg" : "API group not found"
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
