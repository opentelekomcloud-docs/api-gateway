:original_name: ShowDetailsOfAclPolicyV2.html

.. _ShowDetailsOfAclPolicyV2:

Querying Details of an Access Control Policy
============================================

Function
--------

This API is used to query the details of an access control policy.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/acls/{acl_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | acl_id      | Yes       | String | Access control policy ID.                                                                                             |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

   +-----------------------+-----------------------+-------------------------+
   | Parameter             | Type                  | Description             |
   +=======================+=======================+=========================+
   | acl_name              | String                | Name.                   |
   +-----------------------+-----------------------+-------------------------+
   | acl_type              | String                | Type.                   |
   |                       |                       |                         |
   |                       |                       | -  PERMIT (whitelist)   |
   |                       |                       |                         |
   |                       |                       | -  DENY (blacklist)     |
   +-----------------------+-----------------------+-------------------------+
   | acl_value             | String                | Access control objects. |
   +-----------------------+-----------------------+-------------------------+
   | entity_type           | String                | Object type.            |
   |                       |                       |                         |
   |                       |                       | -  IP                   |
   |                       |                       |                         |
   |                       |                       | -  DOMAIN               |
   |                       |                       |                         |
   |                       |                       | -  DOMAIN_ID            |
   +-----------------------+-----------------------+-------------------------+
   | id                    | String                | ID.                     |
   +-----------------------+-----------------------+-------------------------+
   | update_time           | String                | Update time.            |
   +-----------------------+-----------------------+-------------------------+

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

.. code-block::

   {
     "id" : "7eb619ecf2a24943b099833cd24a01ba",
     "acl_name" : "acl_demo",
     "entity_type" : "IP",
     "acl_type" : "PERMIT",
     "acl_value" : "192.168.1.5,192.168.10.1",
     "update_time" : "2020-08-04T08:42:43Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:id. Please refer to the support documentation"
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
