:original_name: AcceptOrRejectEndpointConnections.html

.. _AcceptOrRejectEndpointConnections:

Accepting or Rejecting a VPC Endpoint Connection
================================================

Function
--------

This API is used to accept or reject a VPC endpoint connection for a gateway.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/vpc-endpoint/connections/action

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

   +-----------------+-----------------+------------------+------------------------------+
   | Parameter       | Mandatory       | Type             | Description                  |
   +=================+=================+==================+==============================+
   | action          | Yes             | String           | Allow or reject connections. |
   |                 |                 |                  |                              |
   |                 |                 |                  | -  receive                   |
   |                 |                 |                  |                              |
   |                 |                 |                  | -  reject                    |
   |                 |                 |                  |                              |
   |                 |                 |                  | Enumeration values:          |
   |                 |                 |                  |                              |
   |                 |                 |                  | -  **receive**               |
   |                 |                 |                  |                              |
   |                 |                 |                  | -  **reject**                |
   +-----------------+-----------------+------------------+------------------------------+
   | endpoints       | Yes             | Array of strings | VPC endpoints.               |
   |                 |                 |                  |                              |
   |                 |                 |                  | Array Length: **1 - 50**     |
   +-----------------+-----------------+------------------+------------------------------+

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

   +-------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter   | Type                                                                                                        | Description                                          |
   +=============+=============================================================================================================+======================================================+
   | size        | Integer                                                                                                     | Length of the returned resource list.                |
   +-------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total       | Long                                                                                                        | Number of resources that match the query conditions. |
   +-------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | connections | Array of :ref:`EndpointConnection <acceptorrejectendpointconnections__response_endpointconnection>` objects | Connections.                                         |
   +-------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _acceptorrejectendpointconnections__response_endpointconnection:

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

-  Accept a connection from a VPC endpoint.

   .. code-block::

      {
        "action" : "receive",
        "endpoints" : [ "9fa04c5e-64ec-4106-a014-2ad71ad9997d" ]
      }

-  Disable a VPC endpoint connection.

   .. code-block::

      {
        "action" : "reject",
        "endpoints" : [ "9fa04c5e-64ec-4106-a014-2ad71ad9997d" ]
      }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "connections" : [ {
       "id" : "9cf102d8-aaa0-44cf-8222-fd6f2c073887",
       "marker_id" : 167792784,
       "created_at" : "2021-05-07T14:20:14Z",
       "updated_at" : "2021-05-07T14:30:25Z",
       "domain_id" : "c90f12a0f1ee43bc90a1f4d17bce35bc",
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
