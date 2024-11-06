:original_name: UpdateIngressEipV2.html

.. _UpdateIngressEipV2:

Updating Public Inbound Access Bandwidth of a Gateway
=====================================================

Function
--------

This API is used to update the public inbound access bandwidth of a gateway that uses ELB for load balancing.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/ingress-eip

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

   +-------------------------+-----------------+-----------------+------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                          |
   +=========================+=================+=================+======================================================+
   | bandwidth_size          | No              | Integer         | Public inbound access bandwidth.                     |
   |                         |                 |                 |                                                      |
   |                         |                 |                 | Unit: Mbit/s                                         |
   +-------------------------+-----------------+-----------------+------------------------------------------------------+
   | bandwidth_charging_mode | No              | String          | Billing type of the public inbound access bandwidth. |
   |                         |                 |                 |                                                      |
   |                         |                 |                 | -  bandwidth: billed by bandwidth                    |
   |                         |                 |                 |                                                      |
   |                         |                 |                 | Default: **bandwidth**                               |
   |                         |                 |                 |                                                      |
   |                         |                 |                 | Enumeration values:                                  |
   |                         |                 |                 |                                                      |
   |                         |                 |                 | -  **bandwidth**                                     |
   +-------------------------+-----------------+-----------------+------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 4** Response body parameters

   =========== ====== ==================================
   Parameter   Type   Description
   =========== ====== ==================================
   instance_id String Gateway ID.
   message     String Public access address change task.
   job_id      String Task ID.
   =========== ====== ==================================

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

Updating public inbound access bandwidth of a gateway

.. code-block::

   {
     "bandwidth_size" : 5,
     "bandwidth_charging_mode" : "bandwidth"
   }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "instance_id" : "6a7d71827fd54572b1f31aa9548fcc81",
     "message" : "JOB_ASSIGNED_FOR_UPDATE_0077I:The job JOB-a7c1241c33334490a3fdcd11102bcbda is assigned to the instance 6a7d71827fd54572b1f31aa9548fcc81 for running updating",
     "job_id" : "JOB-a7c1241c33334490a3fdcd11102bcbda"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIC.9211",
     "error_msg" : "update bandwidth size failed"
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

Not Found

.. code-block::

   {
     "error_code" : "APIC.7302",
     "error_msg" : "Instance not found"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIC.9000",
     "error_msg" : "Failed to request internal service"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
202         Accepted
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
