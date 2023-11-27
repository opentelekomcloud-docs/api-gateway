:original_name: ShowDetailsOfInstanceProgressV2_1.html

.. _ShowDetailsOfInstanceProgressV2_1:

Querying the Creation Progress of a Dedicated Gateway
=====================================================

Function
--------

This API is used to query the creation progress of a dedicated gateway.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/progress

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                            |
   +=======================+=======================+========================================================================================+
   | progress              | Integer               | Gateway creation progress.                                                             |
   |                       |                       |                                                                                        |
   |                       |                       | Unit: %                                                                                |
   |                       |                       |                                                                                        |
   |                       |                       | Enumeration values:                                                                    |
   |                       |                       |                                                                                        |
   |                       |                       | -  **30**                                                                              |
   |                       |                       |                                                                                        |
   |                       |                       | -  **50**                                                                              |
   |                       |                       |                                                                                        |
   |                       |                       | -  **80**                                                                              |
   |                       |                       |                                                                                        |
   |                       |                       | -  **90**                                                                              |
   |                       |                       |                                                                                        |
   |                       |                       | -  **100**                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+
   | status                | String                | Gateway creation status.                                                               |
   |                       |                       |                                                                                        |
   |                       |                       | -  creating                                                                            |
   |                       |                       |                                                                                        |
   |                       |                       | -  success                                                                             |
   |                       |                       |                                                                                        |
   |                       |                       | -  failed                                                                              |
   |                       |                       |                                                                                        |
   |                       |                       | Enumeration values:                                                                    |
   |                       |                       |                                                                                        |
   |                       |                       | -  **creating**                                                                        |
   |                       |                       |                                                                                        |
   |                       |                       | -  **success**                                                                         |
   |                       |                       |                                                                                        |
   |                       |                       | -  **failed**                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+
   | error_code            | String                | Error code.                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+
   | error_msg             | String                | Error message.                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+
   | start_time            | Long                  | Time when the gateway creation starts. The time is in the Unix timestamp format.       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+
   | end_time              | Long                  | Time when the gateway creation is completed. The time is in the Unix timestamp format. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

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

-  Gateway created.

   .. code-block::

      {
        "end_time" : 1597390224911,
        "error_code" : null,
        "error_msg" : null,
        "progress" : 100,
        "start_time" : 1597389901161,
        "status" : "success"
      }

-  Gateway is being created.

   .. code-block::

      {
        "end_time" : 1597390224911,
        "error_code" : null,
        "error_msg" : null,
        "progress" : 50,
        "start_time" : 1597389901161,
        "status" : "creating"
      }

-  Gateway creation failed due to insufficient quota.

   .. code-block::

      {
        "end_time" : 1597390224911,
        "error_code" : "APIC.9218",
        "error_msg" : "create failed...",
        "progress" : 0,
        "start_time" : 1597389901161,
        "status" : "failed"
      }

-  Gateway creation failed due to insufficient resources.

   .. code-block::

      {
        "end_time" : 1597390224911,
        "error_code" : "APIC.9219",
        "error_msg" : "create failed...",
        "progress" : 0,
        "start_time" : 1597389901161,
        "status" : "failed"
      }

-  Gateway creation failed due to other reasons.

   .. code-block::

      {
        "end_time" : 1597390224911,
        "error_code" : "APIC.9206",
        "error_msg" : "create failed...",
        "progress" : 0,
        "start_time" : 1597389901161,
        "status" : "failed"
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
200         OK
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
