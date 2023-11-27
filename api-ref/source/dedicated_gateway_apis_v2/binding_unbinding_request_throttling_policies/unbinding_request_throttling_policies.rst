:original_name: BatchDisassociateThrottlingPolicyV2_1.html

.. _BatchDisassociateThrottlingPolicyV2_1:

Unbinding Request Throttling Policies
=====================================

Function
--------

This API is used to unbind request throttling policies from APIs.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/throttle-bindings

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

   +-------------------+-----------+------------------+----------------------------------------------------------------------+
   | Parameter         | Mandatory | Type             | Description                                                          |
   +===================+===========+==================+======================================================================+
   | throttle_bindings | No        | Array of strings | IDs of the request throttling policy binding records to be canceled. |
   +-------------------+-----------+------------------+----------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +---------------+-----------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Parameter     | Type                                                                                                                              | Description                                                                |
   +===============+===================================================================================================================================+============================================================================+
   | success_count | Integer                                                                                                                           | Number of request throttling policies that have been successfully unbound. |
   +---------------+-----------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | failure       | Array of :ref:`ThrottleBindingBatchFailure <batchdisassociatethrottlingpolicyv2_1__response_throttlebindingbatchfailure>` objects | Error message and request throttling policies that fail to be unbound.     |
   +---------------+-----------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

.. _batchdisassociatethrottlingpolicyv2_1__response_throttlebindingbatchfailure:

.. table:: **Table 6** ThrottleBindingBatchFailure

   +------------+--------+-----------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                 |
   +============+========+=============================================================================+
   | bind_id    | String | ID of a request throttling policy binding record that fails to be canceled. |
   +------------+--------+-----------------------------------------------------------------------------+
   | error_code | String | Error code.                                                                 |
   +------------+--------+-----------------------------------------------------------------------------+
   | error_msg  | String | Error message.                                                              |
   +------------+--------+-----------------------------------------------------------------------------+
   | api_id     | String | ID of an API from which unbinding fails.                                    |
   +------------+--------+-----------------------------------------------------------------------------+
   | api_name   | String | Name of the API from which unbinding fails.                                 |
   +------------+--------+-----------------------------------------------------------------------------+

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

Unbinding request throttling policies from APIs

.. code-block::

   {
     "throttle_bindings" : [ "6a6a75b425df416cbdcd7821da30be8d", "b11e5970f732440dbea647580647d57f" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "failure" : [ {
       "bind_id" : "b11e5970f732440dbea647580647d57f",
       "error_code" : "APIG.3012",
       "error_msg" : "The request throttling policy binding record does not exist"
     } ],
     "success_count" : 1
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "parameter action should be \\\"delete\\\""
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
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
