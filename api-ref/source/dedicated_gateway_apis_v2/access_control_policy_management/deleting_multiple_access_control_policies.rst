:original_name: BatchDeleteAclV2_1.html

.. _BatchDeleteAclV2_1:

Deleting Multiple Access Control Policies
=========================================

Function
--------

This API is used to delete multiple access control policies.

Access control policies bound to APIs cannot be deleted.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/acls

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ====== =========================
   Parameter Mandatory Type   Description
   ========= ========= ====== =========================
   action    Yes       String The value must be delete.
   ========= ========= ====== =========================

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------+-----------+------------------+---------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                       |
   +===========+===========+==================+===================================================+
   | acls      | No        | Array of strings | IDs of the access control policies to be deleted. |
   +-----------+-----------+------------------+---------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +---------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter     | Type                                                                                                       | Description                                                            |
   +===============+============================================================================================================+========================================================================+
   | success_count | Integer                                                                                                    | Number of access control policies that have been successfully deleted. |
   +---------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | failure       | Array of :ref:`AclBatchResultFailureResp <batchdeleteaclv2_1__response_aclbatchresultfailureresp>` objects | Error message and access control policies that fail to be deleted.     |
   +---------------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _batchdeleteaclv2_1__response_aclbatchresultfailureresp:

.. table:: **Table 6** AclBatchResultFailureResp

   +------------+--------+----------------------------------------------------------+
   | Parameter  | Type   | Description                                              |
   +============+========+==========================================================+
   | acl_id     | String | ID of an access control policy that fails to be deleted. |
   +------------+--------+----------------------------------------------------------+
   | acl_name   | String | Name of the access control policy.                       |
   +------------+--------+----------------------------------------------------------+
   | error_code | String | Error code.                                              |
   +------------+--------+----------------------------------------------------------+
   | error_msg  | String | Error message.                                           |
   +------------+--------+----------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Deleting multiple access control policies

.. code-block::

   {
     "acls" : [ "7eb619ecf2a24943b099833cd24a01ba", "3a68d39f115d4c128fccd6f624ea6109" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "failure" : [ {
       "acl_id" : "7eb619ecf2a24943b099833cd24a01ba",
       "acl_name" : "acl_demo",
       "error_code" : "APIG.3447",
       "error_msg" : "The access control policy has been bound to APIs"
     } ],
     "success_count" : 1
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value: parameter action should be \\\"delete\\\""
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
     "error_msg" : "The instance does not exist;id:eddc4d25480b4cd6b512f270a1b8b341"
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
