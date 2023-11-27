:original_name: CreateApiAclBindingV2_1.html

.. _CreateApiAclBindingV2_1:

Binding an Access Control Policy to an API
==========================================

Function
--------

This API is used to bind an access control policy to a specified API.

You can bind different access control policies to an API in different environments, but you can bind only one access control policy to the API in each environment.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/acl-bindings

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

   =========== ========= ================ ==========================
   Parameter   Mandatory Type             Description
   =========== ========= ================ ==========================
   acl_id      No        String           Access control policy ID.
   publish_ids No        Array of strings API publication record ID.
   =========== ========= ================ ==========================

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +--------------+-------------------------------------------------------------------------------------------------+----------------------------------------+
   | Parameter    | Type                                                                                            | Description                            |
   +==============+=================================================================================================+========================================+
   | acl_bindings | Array of :ref:`AclApiBindingInfo <createapiaclbindingv2_1__response_aclapibindinginfo>` objects | Access control policy binding records. |
   +--------------+-------------------------------------------------------------------------------------------------+----------------------------------------+

.. _createapiaclbindingv2_1__response_aclapibindinginfo:

.. table:: **Table 5** AclApiBindingInfo

   =========== ====== =========================
   Parameter   Type   Description
   =========== ====== =========================
   id          String Binding record ID.
   api_id      String API ID.
   env_id      String Environment ID.
   acl_id      String Access control policy ID.
   create_time String Binding time.
   =========== ====== =========================

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

Binding an access control policy to an API

.. code-block::

   {
     "acl_id" : "7eb619ecf2a24943b099833cd24a01ba",
     "publish_ids" : [ "40e7162dc6b94bbbbb1a60d2a24b1b0c" ]
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "acl_bindings" : [ {
       "id" : "332c5db1458a477b89b2ea741fec94a3",
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "acl_id" : "7eb619ecf2a24943b099833cd24a01ba",
       "create_time" : "2020-08-04T08:58:03.001228747Z"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:acl_id. Please refer to the support documentation"
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
     "error_code" : "APIG.3006",
     "error_msg" : "Access control policy 7eb619ecf2a24943b099833cd24a01ba does not exist"
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
201         Created
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
