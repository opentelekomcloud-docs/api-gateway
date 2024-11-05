:original_name: ImportApiDefinitionsAsync.html

.. _ImportApiDefinitionsAsync:

Importing APIs Asynchronously
=============================

Function
--------

This API is used to import APIs. The content of the imported file must comply with the Swagger standard. For details about the custom extended fields of APIG, see section "Extended Definition" in the User Guide.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/openapi/async-import

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
   | is_create_group | No              | Boolean         | Whether to create a new group.                                                |
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
   | simple_mode     | No              | Boolean         | Whether to enable fast import.                                                |
   |                 |                 |                 |                                                                               |
   |                 |                 |                 | Default: **false**                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+
   | mock_mode       | No              | Boolean         | Whether to enable the Mock backend.                                           |
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
   | file_name       | Yes             | File            | Request body in JSON or YAML format for importing APIs                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   task_id   String Task ID.
   ========= ====== ===========

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

Importing APIs

.. code-block::

   {
     "is_create_group" : false,
     "group_id" : "d9ce8c9eede54b3f841ec324fe0bfdc2",
     "file_name" : "APIGroup_test.json"
   }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "task_id" : "d9ce8c9eede54b3f841ec324fe0bfdc2"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3603",
     "error_msg" : "The input data is too long"
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
202         Accepted
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
