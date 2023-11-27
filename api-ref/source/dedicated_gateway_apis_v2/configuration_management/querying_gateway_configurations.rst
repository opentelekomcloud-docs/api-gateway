:original_name: ListInstanceConfigsV2_1.html

.. _ListInstanceConfigsV2_1:

Querying Gateway Configurations
===============================

Function
--------

This API is used to query the gateway configurations.

URI
---

GET /v2/{project_id}/apigw/instance/configs

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

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

   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                      | Description                                          |
   +===========+===========================================================================================+======================================================+
   | size      | Integer                                                                                   | Length of the returned resource list.                |
   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                      | Number of resources that match the query conditions. |
   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | configs   | Array of :ref:`InstanceConfig <listinstanceconfigsv2_1__response_instanceconfig>` objects | Quota list.                                          |
   +-----------+-------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listinstanceconfigsv2_1__response_instanceconfig:

.. table:: **Table 5** InstanceConfig

   +-----------------------+-----------------------+----------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                          |
   +=======================+=======================+======================================================================+
   | config_id             | String                | Quota ID.                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------+
   | config_name           | String                | Quota name.                                                          |
   |                       |                       |                                                                      |
   |                       |                       | Enumeration values:                                                  |
   |                       |                       |                                                                      |
   |                       |                       | -  **INSTANCE_NUM_LIMIT**                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------+
   | config_value          | String                | Quota value.                                                         |
   |                       |                       |                                                                      |
   |                       |                       | It indicates the value of the quota for the current gateway.         |
   +-----------------------+-----------------------+----------------------------------------------------------------------+
   | config_time           | String                | Time when the quota is created.                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------+
   | remark                | String                | Quota description.                                                   |
   |                       |                       |                                                                      |
   |                       |                       | -  INSTANCE_NUM_LIMIT: Number of instances that a tenant can create. |
   +-----------------------+-----------------------+----------------------------------------------------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 1,
     "size" : 1,
     "configs" : [ {
       "config_id" : "1",
       "config_name" : "INSTANCE_NUM_LIMIT",
       "config_value" : "5",
       "config_time" : 1597981093255,
       "remark" : "xxx"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:instance_id. Please refer to the support documentation"
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
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
