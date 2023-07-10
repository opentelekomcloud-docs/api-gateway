:original_name: BatchDeleteApiAclBindingV2.html

.. _BatchDeleteApiAclBindingV2:

Unbinding Access Control Policies
=================================

Function
--------

This API is used to unbind multiple access control policies from APIs.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/acl-bindings

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

   +--------------+-----------+------------------+------------------------------------------------------------------+
   | Parameter    | Mandatory | Type             | Description                                                      |
   +==============+===========+==================+==================================================================+
   | acl_bindings | No        | Array of strings | IDs of the access control policy binding records to be canceled. |
   +--------------+-----------+------------------+------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +---------------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | Parameter     | Type                                                                                                         | Description                                                            |
   +===============+==============================================================================================================+========================================================================+
   | success_count | Integer                                                                                                      | Number of access control policies that have been successfully unbound. |
   +---------------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+
   | failure       | Array of :ref:`AclBindingBatchFailure <batchdeleteapiaclbindingv2__response_aclbindingbatchfailure>` objects | Error message and access control policies that fail to be unbound.     |
   +---------------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------+

.. _batchdeleteapiaclbindingv2__response_aclbindingbatchfailure:

.. table:: **Table 6** AclBindingBatchFailure

   +------------+--------+--------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                              |
   +============+========+==========================================================================+
   | bind_id    | String | ID of an access control policy binding record that fails to be canceled. |
   +------------+--------+--------------------------------------------------------------------------+
   | error_code | String | Error code.                                                              |
   +------------+--------+--------------------------------------------------------------------------+
   | error_msg  | String | Error message.                                                           |
   +------------+--------+--------------------------------------------------------------------------+
   | api_id     | String | ID of an API from which unbinding fails.                                 |
   +------------+--------+--------------------------------------------------------------------------+
   | api_name   | String | Name of the API from which unbinding fails.                              |
   +------------+--------+--------------------------------------------------------------------------+

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

.. code-block::

   {
     "acl_bindings" : [ "332c5db1458a477b89b2ea741fec94a3" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "failure" : [ {
       "bind_id" : "3a68d39f115d4c128fccd6f624ea6109",
       "error_code" : "APIG.3010",
       "error_msg" : "The access control policy binding record does not exist"
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
