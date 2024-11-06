:original_name: ShowAppBoundAppQuota.html

.. _ShowAppBoundAppQuota:

Querying Quotas Associated with a Credential
============================================

Function
--------

This API is used to query quotas associated with a specified credential.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/apps/{app_id}/bound-quota

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | app_id      | Yes       | String | App ID.                                                                                                 |
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

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================+
   | app_quota_id          | String                | Credential quota ID.                                                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Quota name. Enter 3 to 255 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed.                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | call_limits           | Integer               | Maximum number of times a credential quota can be called.                                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_unit             | String                | Time unit. The options are SECOND, MINUTE, HOUR, and DAY.                                                                                               |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | Enumeration values:                                                                                                                                     |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | -  **SECOND**                                                                                                                                           |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | -  **MINUTE**                                                                                                                                           |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | -  **HOUR**                                                                                                                                             |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | -  **DAY**                                                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_interval         | Integer               | Time limit of a quota.                                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remark                | String                | Parameter description.                                                                                                                                  |
   |                       |                       |                                                                                                                                                         |
   |                       |                       | Maximum: **255**                                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | reset_time            | String                | Time when the quota is reset for the first time. If this parameter is not specified, the time is calculated based on the first calling time by default. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                                                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bound_app_num         | Integer               | Number of applications bound to the quota policy.                                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "app_quota_id" : "c900c5612dbe451bb43cbcc49cfaf2f3",
     "name" : "ClientQuota_demo",
     "call_limits" : 1000,
     "time_unit" : "DAY",
     "time_interval" : 1,
     "remark" : "remark",
     "reset_time" : "2020-09-20 00:00:00 +0000 +0000",
     "create_time" : "2020-09-19T07:27:47Z",
     "bound_app_num" : 0
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
     "error_code" : "APIG.3002",
     "error_msg" : "App 98df09fb-d459-4cbf-83a7-2b55ca6f3d5d does not exist"
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
