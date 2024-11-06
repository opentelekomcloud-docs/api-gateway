:original_name: ListAclPolicyBindedToApiV2.html

.. _ListAclPolicyBindedToApiV2:

Querying Access Control Policies Bound to an API
================================================

Function
--------

This API is used to query the access control policies that have been bound to a specified API.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/acl-bindings/binded-acls

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

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
   | api_id          | Yes             | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | No              | String          | Environment ID.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_name        | No              | String          | Environment name.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | acl_id          | No              | String          | Access control policy ID.                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | acl_name        | No              | String          | Access control policy name.                                                                                                                                                         |
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

   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                         | Description                                          |
   +===========+==============================================================================================+======================================================+
   | size      | Integer                                                                                      | Length of the returned resource list.                |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                         | Number of resources that match the query conditions. |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | acls      | Array of :ref:`ApiBindAclInfo <listaclpolicybindedtoapiv2__response_apibindaclinfo>` objects | Access control policy list.                          |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listaclpolicybindedtoapiv2__response_apibindaclinfo:

.. table:: **Table 5** ApiBindAclInfo

   +-----------------------+-----------------------+-----------------------------+
   | Parameter             | Type                  | Description                 |
   +=======================+=======================+=============================+
   | acl_id                | String                | Access control policy ID.   |
   +-----------------------+-----------------------+-----------------------------+
   | acl_name              | String                | Access control policy name. |
   +-----------------------+-----------------------+-----------------------------+
   | entity_type           | String                | Object type.                |
   |                       |                       |                             |
   |                       |                       | Enumeration values:         |
   |                       |                       |                             |
   |                       |                       | -  **IP**                   |
   |                       |                       |                             |
   |                       |                       | -  **DOMAIN**               |
   |                       |                       |                             |
   |                       |                       | -  **DOMAIN_ID**            |
   +-----------------------+-----------------------+-----------------------------+
   | acl_type              | String                | Access control type.        |
   |                       |                       |                             |
   |                       |                       | -  PERMIT: whitelist        |
   |                       |                       |                             |
   |                       |                       | -  DENY: blacklist          |
   |                       |                       |                             |
   |                       |                       | Enumeration values:         |
   |                       |                       |                             |
   |                       |                       | -  **PERMIT**               |
   |                       |                       |                             |
   |                       |                       | -  **DENY**                 |
   +-----------------------+-----------------------+-----------------------------+
   | acl_value             | String                | Access control objects.     |
   +-----------------------+-----------------------+-----------------------------+
   | env_id                | String                | Effective environment ID.   |
   +-----------------------+-----------------------+-----------------------------+
   | env_name              | String                | Effective environment name. |
   +-----------------------+-----------------------+-----------------------------+
   | bind_id               | String                | Binding record ID.          |
   +-----------------------+-----------------------+-----------------------------+
   | bind_time             | String                | Binding time.               |
   +-----------------------+-----------------------+-----------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 1,
     "size" : 1,
     "acls" : [ {
       "acl_id" : "7eb619ecf2a24943b099833cd24a01ba",
       "acl_name" : "acl_demo",
       "entity_type" : "IP",
       "acl_type" : "PERMIT",
       "acl_value" : "192.168.1.5,192.168.10.1",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "bind_id" : "332c5db1458a477b89b2ea741fec94a3",
       "bind_time" : "2020-08-04T08:58:03Z"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:acl_name. Please refer to the support documentation"
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
     "error_code" : "APIG.3002",
     "error_msg" : "API 5f918d104dc84480a75166ba99efff21 does not exist"
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
