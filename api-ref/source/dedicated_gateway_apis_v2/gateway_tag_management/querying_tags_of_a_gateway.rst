:original_name: ListInstanceTags.html

.. _ListInstanceTags:

Querying Tags of a Gateway
==========================

Function
--------

This API is used to query all tags of a gateway.

Constraints
-----------

Only users who have been authorized with a policy containing actions apig:instanceTags:list and apig:instances:get can call this API.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/instance-tags

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

   +----------------+------------------------------------------------------------------------------+-----------------------------------------------------+
   | Parameter      | Type                                                                         | Description                                         |
   +================+==============================================================================+=====================================================+
   | resource_id    | String                                                                       | Gateway ID.                                         |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------------+
   | resouce_detail | String                                                                       | Detailed description of the gateway. Not supported. |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------------+
   | resource_name  | String                                                                       | Gateway name.                                       |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------------+
   | tags           | Array of :ref:`TmsKeyValue <listinstancetags__response_tmskeyvalue>` objects | Tags bound to the gateway.                          |
   +----------------+------------------------------------------------------------------------------+-----------------------------------------------------+

.. _listinstancetags__response_tmskeyvalue:

.. table:: **Table 4** TmsKeyValue

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                           |
   +=======================+=======================+=======================================================================================================+
   | key                   | String                | Key.                                                                                                  |
   |                       |                       |                                                                                                       |
   |                       |                       | Include UTF-8 letters, digits, spaces, or special characters ``(_.:=+-@).``                           |
   |                       |                       |                                                                                                       |
   |                       |                       | Do not start with \_sys\_ because it is a system label.                                               |
   |                       |                       |                                                                                                       |
   |                       |                       | Minimum: **1**                                                                                        |
   |                       |                       |                                                                                                       |
   |                       |                       | Maximum: **128**                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | value                 | String                | Value.                                                                                                |
   |                       |                       |                                                                                                       |
   |                       |                       | You can enter letters, digits, and spaces or other special characters ``(_.:/=+-@)`` in UTF-8 format. |
   |                       |                       |                                                                                                       |
   |                       |                       | Minimum: **0**                                                                                        |
   |                       |                       |                                                                                                       |
   |                       |                       | Maximum: **255**                                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

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

.. code-block::

   {
     "resource_id" : "e120108ac331422cb539d8609e9a7bb2",
     "resouce_detail" : null,
     "resource_name" : "apig_instance",
     "tags" : [ {
       "key" : "test-key",
       "value" : "test-vaue"
     } ]
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
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
