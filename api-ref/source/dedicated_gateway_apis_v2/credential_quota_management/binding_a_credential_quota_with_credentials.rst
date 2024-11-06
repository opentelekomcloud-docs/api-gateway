:original_name: AssociateAppsForAppQuota.html

.. _AssociateAppsForAppQuota:

Binding a Credential Quota with Credentials
===========================================

Function
--------

This API is used to bind a credential quota with credentials.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/app-quotas/{app_quota_id}/binding-apps

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

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   ========= ========= ================ ===================
   Parameter Mandatory Type             Description
   ========= ========= ================ ===================
   app_ids   Yes       Array of strings Credential ID List.
   ========= ========= ================ ===================

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------------+-----------------------------------------------+
   | Parameter | Type                                                                                               | Description                                   |
   +===========+====================================================================================================+===============================================+
   | applies   | Array of :ref:`AppQuotaAppBinding <associateappsforappquota__response_appquotaappbinding>` objects | Credential and credential quota binding list. |
   +-----------+----------------------------------------------------------------------------------------------------+-----------------------------------------------+

.. _associateappsforappquota__response_appquotaappbinding:

.. table:: **Table 5** AppQuotaAppBinding

   ============ ====== ====================
   Parameter    Type   Description
   ============ ====== ====================
   app_quota_id String Credential quota ID.
   app_id       String Credential ID.
   bound_time   String Binding time.
   ============ ====== ====================

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

.. code-block::

   {
     "app_ids" : [ "98df09fb-d459-4cbf-83a7-2b55ca6f3d5d" ]
   }

Example Responses
-----------------

**Status code: 201**

OK

.. code-block::

   {
     "applies" : [ {
       "app_id" : "98df09fb-d459-4cbf-83a7-2b55ca6f3d5d",
       "app_quota_id" : "c900c5612dbe451bb43cbcc49cfaf2f3",
       "bound_time" : "2020-09-19T07:43:11.948178051Z"
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
