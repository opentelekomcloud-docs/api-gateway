:original_name: BatchCreateOrDeleteInstanceTags.html

.. _BatchCreateOrDeleteInstanceTags:

Adding or Deleting Tags of a Gateway
====================================

Function
--------

This API is used to add tags to a gateway or delete the tags of a gateway.

Constraints
-----------

Only users who have been authorized with a policy containing actions apig:instances:get, apig:instanceTags:create, and apig:instanceTags:delete can call this API.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/instance-tags/action

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

   +-----------------+-----------------+--------------------------------------------------------------------------------------------+----------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                       | Description                                        |
   +=================+=================+============================================================================================+====================================================+
   | action          | Yes             | String                                                                                     | Operation: create and delete.                      |
   |                 |                 |                                                                                            |                                                    |
   |                 |                 |                                                                                            | Enumeration values:                                |
   |                 |                 |                                                                                            |                                                    |
   |                 |                 |                                                                                            | -  **create**                                      |
   |                 |                 |                                                                                            |                                                    |
   |                 |                 |                                                                                            | -  **delete**                                      |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------+----------------------------------------------------+
   | tags            | Yes             | Array of :ref:`TmsKeyValue <batchcreateordeleteinstancetags__request_tmskeyvalue>` objects | Tags.                                              |
   |                 |                 |                                                                                            |                                                    |
   |                 |                 |                                                                                            | A maximum of 20 tags can be created for a gateway. |
   |                 |                 |                                                                                            |                                                    |
   |                 |                 |                                                                                            | Array Length: **0 - 20**                           |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------+----------------------------------------------------+

.. _batchcreateordeleteinstancetags__request_tmskeyvalue:

.. table:: **Table 4** TmsKeyValue

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                           |
   +=================+=================+=================+=======================================================================================================+
   | key             | No              | String          | Key.                                                                                                  |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Include UTF-8 letters, digits, spaces, or special characters ``(_.:=+-@).``                           |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Do not start with \_sys\_ because it is a system label.                                               |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Minimum: **1**                                                                                        |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Maximum: **128**                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value.                                                                                                |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | You can enter letters, digits, and spaces or other special characters ``(_.:/=+-@)`` in UTF-8 format. |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Minimum: **0**                                                                                        |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Maximum: **255**                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

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

-  Adding tags for a gateway

   .. code-block::

      {
        "action" : "create",
        "tags" : [ {
          "key" : "test-key",
          "value" : "test-value"
        } ]
      }

-  Deleting tags of a gateway

   .. code-block::

      {
        "action" : "delete",
        "tags" : [ {
          "key" : "test-key1",
          "value" : "test-value"
        }, {
          "key" : "test-key2"
        } ]
      }

Example Responses
-----------------

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
     "error_code" : "APIC.9000"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
204         No Content
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
