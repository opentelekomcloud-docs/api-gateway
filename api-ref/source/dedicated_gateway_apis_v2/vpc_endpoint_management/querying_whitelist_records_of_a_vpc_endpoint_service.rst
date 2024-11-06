:original_name: ListEndpointPermissions.html

.. _ListEndpointPermissions:

Querying Whitelist Records of a VPC Endpoint Service
====================================================

Function
--------

This API is used to query the whitelist records of a gateway's VPC endpoint service.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/vpc-endpoint/permissions

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
   | permission      | No              | String          | Permission account ID in format "iam:domain::domain_id". Fuzzy search is supported.                                                                                                 |
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

.. table:: **Table 4** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 5** Response body parameters

   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter   | Type                                                                                              | Description                                          |
   +=============+===================================================================================================+======================================================+
   | size        | Integer                                                                                           | Length of the returned resource list.                |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total       | Long                                                                                              | Number of resources that match the query conditions. |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | permissions | Array of :ref:`EndpointPermission <listendpointpermissions__response_endpointpermission>` objects | Whitelist records.                                   |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listendpointpermissions__response_endpointpermission:

.. table:: **Table 6** EndpointPermission

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   id         String Record ID.
   permission String Permission rules.
   created_at String Creation time.
   ========== ====== =================

**Status code: 401**

.. table:: **Table 7** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 9** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 11** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 12** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 13** Response header parameters

   ============ ====== ===========
   Parameter    Type   Description
   ============ ====== ===========
   x-request-id String Request ID.
   ============ ====== ===========

.. table:: **Table 14** Response body parameters

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
     "total" : 2,
     "size" : 1,
     "permissions" : [ {
       "id" : "e4a7ba21-1e5c-43cc-977d-4aeeacb937ec",
       "permission" : "iam:domain::821a2d452de64bcdb52319967f8a06b9",
       "created_at" : "2021-05-07T14:10:49Z"
     } ]
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
