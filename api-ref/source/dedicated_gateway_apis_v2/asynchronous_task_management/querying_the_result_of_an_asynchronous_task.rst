:original_name: ShowAsyncTaskResult.html

.. _ShowAsyncTaskResult:

Querying the Result of an Asynchronous Task
===========================================

Function
--------

This API is used to query the result of an asynchronous task.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/async-tasks/{task_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | task_id     | Yes       | String | Asynchronous task ID.                                                                                   |
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

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | task_id               | String                | Task ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_status           | String                | Task status. Options: waiting, processing, succeed, and failed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  **waiting**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                       |                       | -  **processing**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                       |                       | -  **succeed**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                       |                       | -  **failed**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_type             | String                | Task type. Options: import_api and export_api. Both types of tasks are asynchronous.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  **import_api**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                       |                       | -  **export_api**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | task_result           | String                | Task result. A string can be converted into a JSON object. If task_type is set to import_api, the fields include group_id, success (array), failure (array), swagger (structure), and ignore (array). The success array contains four fields: id (ID of a successfully imported API), method (API request method), path (API request path), and action (update or create). The failure array also contains four fields: method (API request method), path (API request path), error_code (import error code), and error_msg (import error message). The swagger structure contains two fields: id (Swagger file ID) and result (import result). The ignore array has two elements: method (API request method) and path (API request path). If task_type is set to export_api, the fields include file_type and content. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

-  Example 1

   .. code-block::

      {
        "task_id" : "d9ce8c9eede54b3f841ec324fe0bfdc2",
        "task_status" : "succeed",
        "task_type" : "import_api",
        "task_result" : "{\"success\":[{\"id\":\"ee93ce6815f04896b301452982b92222\",\"action\":\"create\",\"method\":\"GET\",\"path\":\"/test1\"}],\"failure\":[],\"swagger\":{\"id\":\"de1852ab6c5e4090b0bd88a02058e650\",\"result\":\"Success\"},\"group_id\":\"9100ae30705947cc9543d37cd7fb388c\"}"
      }

-  Example 2

   .. code-block::

      {
        "task_id" : "d6e8834b6f0f4711a2fa5345e5b60833",
        "task_status" : "succeed",
        "task_type" : "export_api",
        "task_result" : "{\"FileName\":\"test8-RELEASE-all-2023-07-11-19:54:22\",\"FileType\":\".json\",\"Comment\":\"{\\n\\t\\\"swagger\\\": \\\"2.0\\\",\\n\\t\\\"info\\\": {\\n\\t\\t\\\"title\\\": \\\"test8\\\",\\n\\t\\t\\\"version\\\": \\\"2023-07-11-19:54:22\\\"\\n\\t},\\n\\t\\\"host\\\": \\\"xxx.com\\\",\\n\\t\\\"paths\\\": {\\n\\t\\t\\\"/test1\\\": {\\n\\t\\t\\t\\\"get\\\": {\\n\\t\\t\\t\\t\\\"security\\\": [\\n\\t\\t\\t\\t\\t{\\n\\t\\t\\t\\t\\t\\t\\\"apig-auth-app\\\": []\\n\\t\\t\\t\\t\\t}\\n\\t\\t\\t\\t],\\n\\t\\t\\t\\t\\\"schemes\\\": [\\n\\t\\t\\t\\t\\t\\\"https\\\"\\n\\t\\t\\t\\t],\\n\\t\\t\\t\\t\\\"operationId\\\": \\\"API_zjev\\\",\\n\\t\\t\\t\\t\\\"responses\\\": {\\n\\t\\t\\t\\t\\t\\\"default\\\": {\\n\\t\\t\\t\\t\\t\\t\\\"$ref\\\": \\\"#/responses/default\\\"\\n\\t\\t\\t\\t\\t},\\n\\t\\t\\t\\t\\t\\\"x-apigateway-result-failure-sample\\\": \\\"\\\",\\n\\t\\t\\t\\t\\t\\\"x-apigateway-result-normal-sample\\\": \\\"\\\"\\n\\t\\t\\t\\t},\\n\\t\\t\\t\\t\\\"x-apigateway-backend\\\": {\\n\\t\\t\\t\\t\\t\\\"mockEndpoints\\\": {\\n\\t\\t\\t\\t\\t\\t\\\"description\\\": \\\"\\\",\\n\\t\\t\\t\\t\\t\\t\\\"result-content\\\": \\\"not ok\\\"\\n\\t\\t\\t\\t\\t},\\n\\t\\t\\t\\t\\t\\\"type\\\": \\\"MOCK\\\"\\n\\t\\t\\t\\t},\\n\\t\\t\\t\\t\\\"x-apigateway-cors\\\": false,\\n\\t\\t\\t\\t\\\"x-apigateway-match-mode\\\": \\\"NORMAL\\\",\\n\\t\\t\\t\\t\\\"x-apigateway-request-type\\\": \\\"public\\\"\\n\\t\\t\\t}\\n\\t\\t}\\n\\t},\\n\\t\\\"responses\\\": {\\n\\t\\t\\\"default\\\": {\\n\\t\\t\\t\\\"description\\\": \\\"response example\\\"\\n\\t\\t}\\n\\t},\\n\\t\\\"securityDefinitions\\\": {\\n\\t\\t\\\"apig-auth-app\\\": {\\n\\t\\t\\t\\\"type\\\": \\\"apiKey\\\",\\n\\t\\t\\t\\\"name\\\": \\\"Authorization\\\",\\n\\t\\t\\t\\\"in\\\": \\\"header\\\",\\n\\t\\t\\t\\\"x-apigateway-auth-type\\\": \\\"AppSigv1\\\"\\n\\t\\t},\\n\\t\\t\\\"apig-auth-app-header\\\": {\\n\\t\\t\\t\\\"type\\\": \\\"apiKey\\\",\\n\\t\\t\\t\\\"name\\\": \\\"Authorization\\\",\\n\\t\\t\\t\\\"in\\\": \\\"header\\\",\\n\\t\\t\\t\\\"x-apigateway-auth-opt\\\": {\\n\\t\\t\\t\\t\\\"appcode-auth-type\\\": \\\"header\\\"\\n\\t\\t\\t},\\n\\t\\t\\t\\\"x-apigateway-auth-type\\\": \\\"AppSigv1\\\"\\n\\t\\t},\\n\\t\\t\\\"apig-auth-iam\\\": {\\n\\t\\t\\t\\\"type\\\": \\\"apiKey\\\",\\n\\t\\t\\t\\\"name\\\": \\\"unused\\\",\\n\\t\\t\\t\\\"in\\\": \\\"header\\\",\\n\\t\\t\\t\\\"x-apigateway-auth-type\\\": \\\"IAM\\\"\\n\\t\\t}\\n\\t}\\n,\\n\\t\\\"x-apigateway-responses\\\": {}\\n}\"}"
      }

-  Example 3

   .. code-block::

      {
        "task_id" : "f01d2772ea4944408fa544c8ae5a9999",
        "task_status" : "failed",
        "task_type" : "import_api",
        "task_result" : "{\"error_code\":\"APIG.3201\",\"error_msg\":\"The API group name already exists\"}"
      }

-  Example 4

   .. code-block::

      {
        "task_id" : "4dfbf6acaacf4c41a8b3c50daa90d3dc",
        "task_status" : "processing",
        "task_type" : "import_api",
        "task_result" : ""
      }

-  Example 5

   .. code-block::

      {
        "task_id" : "c3b78a52fb28461aab92bf6c6989f731",
        "task_status" : "waiting",
        "task_type" : "import_api",
        "task_result" : ""
      }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2001",
     "error_msg" : "The request parameters must be specified,parameterName:task_id. Please refer to the support documentation"
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
     "error_code" : "APIG.3093",
     "error_msg" : "The asynchronous task d9ce8c9eede54b3f841ec324fe0bfdc2 does not exist"
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
