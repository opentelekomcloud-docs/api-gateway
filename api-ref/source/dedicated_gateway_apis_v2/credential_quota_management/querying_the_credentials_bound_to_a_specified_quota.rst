:original_name: ListAppQuotaBoundApps.html

.. _ListAppQuotaBoundApps:

Querying the Credentials Bound to a Specified Quota
===================================================

Function
--------

This API is used to query the credentials bound to a credential quota. Fuzzy match by credential name is supported.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/app-quotas/{app_quota_id}/bound-apps

.. table:: **Table 1** Path Parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                             |
   +==============+===========+========+=========================================================================================================+
   | project_id   | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id  | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | app_quota_id | Yes       | String | Credential Quota ID                                                                                     |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================+
   | offset          | No              | Long            | Offset from which the query starts. If the value is less than 0, it is automatically converted to 0.                                                                                |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Default: **0**                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of items displayed on each page. A value less than or equal to 0 will be automatically converted to 20, and a value greater than 500 will be automatically converted to 500. |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Maximum: **500**                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Default: **20**                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_name        | No              | String          | Credential name.                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                      | Description                                          |
   +===========+===========================================================================================+======================================================+
   | size      | Integer                                                                                   | Length of the returned resource list.                |
   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                      | Number of resources that match the query conditions. |
   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | apps      | Array of :ref:`AppQuotaAppInfo <listappquotaboundapps__response_appquotaappinfo>` objects | Credentials.                                         |
   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listappquotaboundapps__response_appquotaappinfo:

.. table:: **Table 5** AppQuotaAppInfo

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                           |
   +=======================+=======================+=======================================================================================================================+
   | app_id                | String                | Credential ID.                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Credential name.                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Credential status:                                                                                                    |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  1: enabled                                                                                                         |
   |                       |                       |                                                                                                                       |
   |                       |                       | -  2: disabled                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | app_key               | String                | Credential key.                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | remark                | String                | Credential description.                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | register_time         | String                | Creation time.                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time.                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | app_quota_id          | String                | Credential quota ID.                                                                                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | app_quota_name        | String                | Quota name. Enter 3 to 255 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | bound_time            | String                | Binding time.                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 500**

.. table:: **Table 10** Response body parameters

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
     "total" : 1,
     "size" : 1,
     "apps" : [ {
       "app_id" : "98df09fb-d459-4cbf-83a7-2b55ca6f3d5d",
       "app_key" : "9b93db07-4634-4b7a-99d8-869933ed055d",
       "app_quota_name" : "ClientQuota_demo",
       "bound_time" : "2020-09-19T07:43:11Z",
       "name" : "app-demo",
       "register_time" : "2020-09-18T09:25:19Z",
       "status" : 1,
       "update_time" : "2020-09-18T09:25:19Z"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:app_name. Please refer to the support documentation"
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
     "error_msg" : "The App quota c900c5612dbe451bb43cbcc49cfaf2f3 does not exist"
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
