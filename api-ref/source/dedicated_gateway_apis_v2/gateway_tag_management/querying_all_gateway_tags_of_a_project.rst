:original_name: ListProjectInstanceTags.html

.. _ListProjectInstanceTags:

Querying All Gateway Tags of a Project
======================================

Function
--------

This API is used to query all gateway tags of a project.

Constraints
-----------

Only users who have been authorized with a policy containing action apig:instanceTags:list can call this API.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instance-tags

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

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

   +-----------+---------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter | Type                                                                                  | Description                                |
   +===========+=======================================================================================+============================================+
   | tags      | Array of :ref:`TmsKeyValues <listprojectinstancetags__response_tmskeyvalues>` objects | Tags bound to all gateways in the project. |
   +-----------+---------------------------------------------------------------------------------------+--------------------------------------------+

.. _listprojectinstancetags__response_tmskeyvalues:

.. table:: **Table 4** TmsKeyValues

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
   | values                | Array of strings      | Value.                                                                                                |
   |                       |                       |                                                                                                       |
   |                       |                       | You can enter letters, digits, and spaces or other special characters ``(_.:/=+-@)`` in UTF-8 format. |
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
     "tags" : [ {
       "key" : "test-key",
       "values" : [ "test-value1", "test-value2" ]
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
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
