:original_name: ListEndpointConnections.html

.. _ListEndpointConnections:

Querying VPC Endpoint Connections
=================================

Function
--------

This API is used to query the VPC endpoint connections of a gateway.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/vpc-endpoint/connections

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
   | id              | No              | String          | Unique VPC endpoint ID.                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | marker_id       | No              | Integer         | Packet ID of a VPC endpoint.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Connection status of a VPC endpoint. Options:                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  pendingAcceptance                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  accepted                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  rejected                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  failed                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  **pendingAcceptance**                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  **accepted**                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  **rejected**                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  **failed**                                                                                                                                                                       |
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
   | connections | Array of :ref:`EndpointConnection <listendpointconnections__response_endpointconnection>` objects | Connections.                                         |
   +-------------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listendpointconnections__response_endpointconnection:

.. table:: **Table 6** EndpointConnection

   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                            |
   +=======================+=======================+========================================================================+
   | id                    | String                | Connection ID.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | marker_id             | Integer               | Connection packet ID.                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | created_at            | String                | Connection creation time. UTC time in the format YYYY-MM-DDTHH:MM:SSZ. |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | updated_at            | String                | Connection update time. UTC time in the format YYYY-MM-DDTHH:MM:SSZ.   |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | domain_id             | String                | Domain ID.                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------+
   | status                | String                | Connection status.                                                     |
   |                       |                       |                                                                        |
   |                       |                       | -  pendingAcceptance                                                   |
   |                       |                       |                                                                        |
   |                       |                       | -  creating                                                            |
   |                       |                       |                                                                        |
   |                       |                       | -  accepted                                                            |
   |                       |                       |                                                                        |
   |                       |                       | -  rejected                                                            |
   |                       |                       |                                                                        |
   |                       |                       | -  failed                                                              |
   |                       |                       |                                                                        |
   |                       |                       | -  deleting                                                            |
   |                       |                       |                                                                        |
   |                       |                       | Enumeration values:                                                    |
   |                       |                       |                                                                        |
   |                       |                       | -  **pendingAcceptance**                                               |
   |                       |                       |                                                                        |
   |                       |                       | -  **creating**                                                        |
   |                       |                       |                                                                        |
   |                       |                       | -  **accepted**                                                        |
   |                       |                       |                                                                        |
   |                       |                       | -  **rejected**                                                        |
   |                       |                       |                                                                        |
   |                       |                       | -  **failed**                                                          |
   |                       |                       |                                                                        |
   |                       |                       | -  **deleting**                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------+

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
     "connections" : [ {
       "id" : "76ad893c-6a1e-4055-8019-fe9c9bd3204d",
       "marker_id" : 167960098,
       "created_at" : "2021-04-29T02:12:44Z",
       "updated_at" : "2021-04-29T02:12:45Z",
       "domain_id" : "b70fde8e849b4e76a61dd8aa0ec05c81",
       "status" : "accepted"
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
