:original_name: ListApisBindedToAclPolicyV2.html

.. _ListApisBindedToAclPolicyV2:

Querying APIs Bound with an Access Control Policy
=================================================

Function
--------

This API is used to query the APIs to which an access control policy has been bound.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/acl-bindings/binded-apis

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
   | acl_id          | Yes             | String          | Access control policy ID.                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_id          | No              | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_name        | No              | String          | API name.                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | No              | String          | Environment ID.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | No              | String          | API group ID.                                                                                                                                                                       |
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

   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                          | Description                                          |
   +===========+===============================================================================================+======================================================+
   | size      | Integer                                                                                       | Length of the returned resource list.                |
   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                          | Number of resources that match the query conditions. |
   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | apis      | Array of :ref:`AclBindApiInfo <listapisbindedtoaclpolicyv2__response_aclbindapiinfo>` objects | API list.                                            |
   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listapisbindedtoaclpolicyv2__response_aclbindapiinfo:

.. table:: **Table 5** AclBindApiInfo

   +------------+--------+-----------------------------------------------------------+
   | Parameter  | Type   | Description                                               |
   +============+========+===========================================================+
   | api_id     | String | API ID.                                                   |
   +------------+--------+-----------------------------------------------------------+
   | api_name   | String | API name.                                                 |
   +------------+--------+-----------------------------------------------------------+
   | api_type   | Long   | API type.                                                 |
   +------------+--------+-----------------------------------------------------------+
   | api_remark | String | API description.                                          |
   +------------+--------+-----------------------------------------------------------+
   | env_id     | String | ID of the environment in which the policy takes effect.   |
   +------------+--------+-----------------------------------------------------------+
   | env_name   | String | Name of the environment in which the policy takes effect. |
   +------------+--------+-----------------------------------------------------------+
   | bind_id    | String | Binding record ID.                                        |
   +------------+--------+-----------------------------------------------------------+
   | group_name | String | API group name.                                           |
   +------------+--------+-----------------------------------------------------------+
   | bind_time  | String | Binding time.                                             |
   +------------+--------+-----------------------------------------------------------+
   | publish_id | String | API publication record ID.                                |
   +------------+--------+-----------------------------------------------------------+

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
     "apis" : [ {
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "api_name" : "Api_http",
       "group_name" : "api_group_001",
       "api_type" : 1,
       "api_remark" : "Web backend API",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "bind_id" : "332c5db1458a477b89b2ea741fec94a3",
       "bind_time" : "2020-08-04T08:58:03Z",
       "publish_id" : "40e7162dc6b94bbbbb1a60d2a24b1b0c"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:api_name. Please refer to the support documentation"
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
