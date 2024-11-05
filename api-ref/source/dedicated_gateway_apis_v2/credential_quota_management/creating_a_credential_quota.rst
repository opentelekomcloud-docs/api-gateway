:original_name: CreateAppQuota.html

.. _CreateAppQuota:

Creating a Credential Quota
===========================

Function
--------

Creating a Credential Quota

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/app-quotas

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

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================+
   | name            | Yes             | String          | Quota name. Start with a letter. Use letters, digits, or underscores (_).                                                                               |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Minimum: **3**                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Maximum: **255**                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | call_limits     | Yes             | Integer         | Maximum number of times a credential quota can be called.                                                                                               |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Minimum: **1**                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Maximum: **2147483647**                                                                                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_unit       | Yes             | String          | Time unit. The options are SECOND, MINUTE, HOUR, and DAY.                                                                                               |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Enumeration values:                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | -  **SECOND**                                                                                                                                           |
   |                 |                 |                 | -  **MINUTE**                                                                                                                                           |
   |                 |                 |                 | -  **HOUR**                                                                                                                                             |
   |                 |                 |                 | -  **DAY**                                                                                                                                              |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_interval   | Yes             | Integer         | Time interval for throttling.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Minimum: **1**                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Maximum: **2147483647**                                                                                                                                 |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | reset_time      | No              | String          | Time when the quota is reset for the first time. If this parameter is not specified, the time is calculated based on the first calling time by default. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remark          | No              | String          | Parameter description.                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Brackets (<>) are not supported.                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                         |
   |                 |                 |                 | Maximum: **255**                                                                                                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

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
   |                       |                       | -  **MINUTE**                                                                                                                                           |
   |                       |                       | -  **HOUR**                                                                                                                                             |
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

.. table:: **Table 5** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 500**

.. table:: **Table 9** Response body parameters

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
     "call_limits" : 1000,
     "name" : "ClientQuota_demo",
     "reset_time" : "2020-09-20 00:00:00",
     "time_interval" : 1,
     "time_unit" : "DAY"
   }

Example Responses
-----------------

**Status code: 201**

OK

.. code-block::

   {
     "app_quota_id" : "c900c5612dbe451bb43cbcc49cfaf2f3",
     "call_limits" : 1000,
     "create_time" : "2020-09-19T15:27:47.60571141+08:00",
     "name" : "ClientQuota_demo",
     "reset_time" : "2020-09-20 00:00:00",
     "time_interval" : 1,
     "time_unit" : "DAY"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3325",
     "error_msg" : "The API quota name already exists"
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
