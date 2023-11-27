:original_name: UpdateAclStrategyV2_1.html

.. _UpdateAclStrategyV2_1:

Modifying an Access Control Policy
==================================

Function
--------

This API is used to modify an access control policy. Only attributes acl_name, acl_type, and acl_value can be modified.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/acls/{acl_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | acl_id      | Yes       | String | Access control policy ID.                                                                               |
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

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================+
   | acl_name        | Yes             | String          | Access control policy name. It can contain 3 to 64 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed.                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | acl_type        | Yes             | String          | Type.                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  PERMIT (whitelist)                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  DENY (blacklist)                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  **PERMIT**                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  **DENY**                                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | acl_value       | Yes             | String          | One or more objects from which the access will be controlled. Separate multiple objects with commas.                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  If entity_type is set to IP, enter up to 100 IP addresses.                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  If entity_type is set to DOMAIN, enter account names. Each account name can contain up to 64 ASCII characters except commas (,). Do not use only digits. The total length cannot exceed 1024 characters. |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  If entity_type is set to DOMAIN_ID, enter account IDs. For details about how to obtain an account ID, see "Appendix" > "Obtaining an Account Name and Account ID" in this document.                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | entity_type     | Yes             | String          | Object type.                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  IP: IP address.                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  DOMAIN: Account name.                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  DOMAIN_ID: Account ID.                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  **IP**                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  **DOMAIN**                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                             |
   |                 |                 |                 | -  **DOMAIN_ID**                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

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

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

Updating an access control policy to allow access from specified IP addresses

.. code-block::

   {
     "acl_name" : "acl_demo",
     "entity_type" : "IP",
     "acl_type" : "PERMIT",
     "acl_value" : "192.168.1.5,192.168.10.1"
   }

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
     "update_time" : "2020-08-04T08:54:55.975856802Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:acl_type. Please refer to the support documentation"
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
