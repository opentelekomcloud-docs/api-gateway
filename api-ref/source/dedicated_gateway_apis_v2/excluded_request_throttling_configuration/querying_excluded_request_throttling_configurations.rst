:original_name: ListSpecialThrottlingConfigurationsV2_0.html

.. _ListSpecialThrottlingConfigurationsV2_0:

Querying Excluded Request Throttling Configurations
===================================================

Function
--------

This API is used to query all excluded configurations of a request throttling policy.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/throttles/{throttle_id}/throttle-specials

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | throttle_id | Yes       | String | Request throttling policy ID.                                                                           |
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
   | object_type     | No              | String          | Object type, which can be APP or USER.                                                                                                                                              |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_name        | No              | String          | Name of an excluded app.                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user            | No              | String          | Name of an excluded user.                                                                                                                                                           |
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

   +-------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter         | Type                                                                                                                | Description                                          |
   +===================+=====================================================================================================================+======================================================+
   | size              | Integer                                                                                                             | Length of the returned resource list.                |
   +-------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total             | Long                                                                                                                | Number of resources that match the query conditions. |
   +-------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | throttle_specials | Array of :ref:`ThrottleSpecialInfo <listspecialthrottlingconfigurationsv2_0__response_throttlespecialinfo>` objects | Excluded configuration list.                         |
   +-------------------+---------------------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listspecialthrottlingconfigurationsv2_0__response_throttlespecialinfo:

.. table:: **Table 5** ThrottleSpecialInfo

   +-------------+---------+--------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                |
   +=============+=========+============================================================================================+
   | id          | String  | Excluded configuration ID.                                                                 |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | call_limits | Integer | Maximum number of times an excluded object can access an API within the throttling period. |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | apply_time  | String  | Throttling period.                                                                         |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | app_name    | String  | App name.                                                                                  |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | app_id      | String  | App ID.                                                                                    |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | object_id   | String  | ID of an object specified in the excluded configuration.                                   |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | object_type | String  | Excluded object type, which can be APP or USER.                                            |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | object_name | String  | Name of an app or a tenant to which the excluded configuration applies.                    |
   +-------------+---------+--------------------------------------------------------------------------------------------+
   | throttle_id | String  | Request throttling policy ID.                                                              |
   +-------------+---------+--------------------------------------------------------------------------------------------+

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
     "throttle_specials" : [ {
       "call_limits" : 200,
       "app_name" : "app_demo",
       "object_name" : "app_demo",
       "object_id" : "356de8eb7a8742168586e5daf5339965",
       "throttle_id" : "3437448ad06f4e0c91a224183116e965",
       "apply_time" : "2020-08-04T02:40:56Z",
       "id" : "a3e9ff8db55544ed9db91d8b048770c0",
       "app_id" : "356de8eb7a8742168586e5daf5339965",
       "object_type" : "APP"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:app_name. Please refer to the support documentation"
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
     "error_code" : "APIG.3005",
     "error_msg" : "Request throttling policy 3437448ad06f4e0c91a224183116e965 does not exist"
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
