:original_name: AddEndpointPermissions.html

.. _AddEndpointPermissions:

Adding Whitelist Records for a VPC Endpoint Service
===================================================

Function
--------

This API is used to add whitelist records in batches for a gateway's VPC endpoint service.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/vpc-endpoint/permissions/batch-add

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

   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                           |
   +=================+=================+==================+=======================================================================================================================================+
   | permissions     | Yes             | Array of strings | Whitelist records. Each whitelist record is in the format of "iam:domain::Authorized_account_ID".                                     |
   |                 |                 |                  |                                                                                                                                       |
   |                 |                 |                  | The account ID contains 32 characters, including only letters (a-f) and digits. An asterisk (``*``) means that all users have access. |
   |                 |                 |                  |                                                                                                                                       |
   |                 |                 |                  | Array Length: **1 - 50**                                                                                                              |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 5** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================+
   | permissions           | Array of strings      | Whitelist records. Each whitelist record is in the format of "iam:domain::Authorized_account_ID".                                     |
   |                       |                       |                                                                                                                                       |
   |                       |                       | The account ID contains 32 characters, including only letters (a-f) and digits. An asterisk (``*``) means that all users have access. |
   |                       |                       |                                                                                                                                       |
   |                       |                       | Array Length: **1 - 50**                                                                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 6** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 8** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 10** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 12** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 13** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Add whitelist records for a vpc endpoint service.

.. code-block::

   {
     "permissions" : [ "iam:domain::7cc2018e40394f7c9692f1713e76234d" ]
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "permissions" : [ "iam:domain::930ba6b0ea64457e8ed1861e596c7a9a" ]
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "APIC.7102",
     "error_msg" : "Incorrect token or token resolution failed"
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "APIC.7106",
     "error_msg" : "No permissions to request for the method"
   }

**Status code: 404**

Resource Not Found

.. code-block::

   {
     "error_code" : "APIC.7314",
     "error_msg" : "Endpoint service not found"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIC.9007",
     "error_msg" : "Failed to execute VCPEP request"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
401         Unauthorized
403         Forbidden
404         Resource Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
