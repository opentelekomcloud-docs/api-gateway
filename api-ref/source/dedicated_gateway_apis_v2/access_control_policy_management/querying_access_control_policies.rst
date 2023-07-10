:original_name: ListAclStrategiesV2.html

.. _ListAclStrategiesV2:

Querying Access Control Policies
================================

Function
--------

This API is used to query all the access control policies.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/acls

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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
   | id              | No              | String          | Access control policy ID.                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Access control policy name.                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | acl_type        | No              | String          | Type.                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  PERMIT (whitelist)                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  DENY (blacklist)                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | entity_type     | No              | String          | Object types.                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  IP                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  DOMAIN                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | precise_search  | No              | String          | Parameter name (name) for exact matching.                                                                                                                                           |
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

   +-----------+-----------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                                | Description                                          |
   +===========+=====================================================================================================+======================================================+
   | size      | Integer                                                                                             | Length of the returned resource list.                |
   +-----------+-----------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                                | Number of resources that match the query conditions. |
   +-----------+-----------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | acls      | Array of :ref:`ApiAclInfoWithBindNum <listaclstrategiesv2__response_apiaclinfowithbindnum>` objects | Access control policy list.                          |
   +-----------+-----------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listaclstrategiesv2__response_apiaclinfowithbindnum:

.. table:: **Table 5** ApiAclInfoWithBindNum

   +-----------------------+-----------------------+-----------------------------+
   | Parameter             | Type                  | Description                 |
   +=======================+=======================+=============================+
   | acl_name              | String                | Access control policy name. |
   +-----------------------+-----------------------+-----------------------------+
   | acl_type              | String                | Type.                       |
   |                       |                       |                             |
   |                       |                       | -  PERMIT (whitelist)       |
   |                       |                       |                             |
   |                       |                       | -  DENY (blacklist)         |
   +-----------------------+-----------------------+-----------------------------+
   | acl_value             | String                | Access control objects.     |
   +-----------------------+-----------------------+-----------------------------+
   | bind_num              | Integer               | Number of APIs.             |
   +-----------------------+-----------------------+-----------------------------+
   | entity_type           | String                | Object type.                |
   |                       |                       |                             |
   |                       |                       | -  IP                       |
   |                       |                       |                             |
   |                       |                       | -  DOMAIN                   |
   |                       |                       |                             |
   |                       |                       | -  DOMAIN_ID                |
   +-----------------------+-----------------------+-----------------------------+
   | id                    | String                | Access control policy ID.   |
   +-----------------------+-----------------------+-----------------------------+
   | update_time           | String                | Update time.                |
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
       "bind_num" : 0,
       "id" : "7eb619ecf2a24943b099833cd24a01ba",
       "acl_name" : "acl_demo",
       "entity_type" : "IP",
       "acl_type" : "PERMIT",
       "acl_value" : "192.168.1.5,192.168.10.1",
       "update_time" : "2020-08-04T08:42:43Z"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:name. Please refer to the support documentation"
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
