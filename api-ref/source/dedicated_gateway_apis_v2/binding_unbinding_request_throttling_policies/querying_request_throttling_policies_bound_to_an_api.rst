:original_name: ListRequestThrottlingPoliciesBindedToApiV2.html

.. _ListRequestThrottlingPoliciesBindedToApiV2:

Querying Request Throttling Policies Bound to an API
====================================================

Function
--------

This API is used to query the request throttling policies that have been bound to an API. Only one request throttling policy can be bound to an API in an environment.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/throttle-bindings/binded-throttles

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
   | api_id          | Yes             | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | throttle_id     | No              | String          | Request throttling policy ID.                                                                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | throttle_name   | No              | String          | Request throttling policy name.                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | No              | String          | Environment ID.                                                                                                                                                                     |
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

   +-----------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                                         | Description                                          |
   +===========+==============================================================================================================+======================================================+
   | size      | Integer                                                                                                      | Length of the returned resource list.                |
   +-----------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                                         | Number of resources that match the query conditions. |
   +-----------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | throttles | Array of :ref:`ThrottleForApi <listrequestthrottlingpoliciesbindedtoapiv2__response_throttleforapi>` objects | Request throttling policy list.                      |
   +-----------+--------------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listrequestthrottlingpoliciesbindedtoapiv2__response_throttleforapi:

.. table:: **Table 5** ThrottleForApi

   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                 | Type                  | Description                                                                                                                                                                                                                                                                 |
   +===========================+=======================+=============================================================================================================================================================================================================================================================================+
   | app_call_limits           | Integer               | Maximum number of times the API can be accessed by an app within the same period. The value of this parameter cannot exceed the user call limit. The maximum value is 2,147,483,647. Enter a positive integer.                                                              |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                      | String                | Request throttling policy name. It can contain 3 to 64 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                           |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_unit                 | String                | Time unit for limiting the number of API calls.                                                                                                                                                                                                                             |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | Enumeration values:                                                                                                                                                                                                                                                         |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **SECOND**                                                                                                                                                                                                                                                               |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **MINUTE**                                                                                                                                                                                                                                                               |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **HOUR**                                                                                                                                                                                                                                                                 |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **DAY**                                                                                                                                                                                                                                                                  |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | remark                    | String                | Description of the request throttling policy, which can contain a maximum of 255 characters.                                                                                                                                                                                |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_call_limits           | Integer               | Maximum number of times an API can be accessed within a specified period. The value of this parameter cannot exceed the default limit 200 TPS. You can change the default limit to meet service requirements. The maximum value is 2,147,483,647. Enter a positive integer. |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                      | Integer               | Type of the request throttling policy.                                                                                                                                                                                                                                      |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  1: API-based, limiting the maximum number of times a single API bound to the policy can be called within the specified period.                                                                                                                                           |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  2: API-shared, limiting the maximum number of times all APIs bound to the policy can be called within the specified period.                                                                                                                                              |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | Enumeration values:                                                                                                                                                                                                                                                         |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **1**                                                                                                                                                                                                                                                                    |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **2**                                                                                                                                                                                                                                                                    |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_adaptive_control   | String                | Indicates whether to enable dynamic request throttling.                                                                                                                                                                                                                     |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  TRUE                                                                                                                                                                                                                                                                     |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  FALSE                                                                                                                                                                                                                                                                    |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | Currently, this parameter is not supported.                                                                                                                                                                                                                                 |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_call_limits          | Integer               | Maximum number of times the API can be accessed by a user within the same period. The value of this parameter cannot exceed the Max. API Requests. The maximum value is 2,147,483,647. Enter a positive integer.                                                            |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_interval             | Integer               | Period of time for limiting the number of API calls. This parameter applies with each API call limit. The maximum value is 2,147,483,647. Enter a positive integer.                                                                                                         |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ip_call_limits            | Integer               | Maximum number of times the API can be accessed by an IP address within the same period. The value of this parameter cannot exceed the API call limit. The maximum value is 2,147,483,647. Enter a positive integer.                                                        |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                        | String                | Request throttling policy ID.                                                                                                                                                                                                                                               |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bind_num                  | Integer               | Number of APIs to which the request throttling policy has been bound.                                                                                                                                                                                                       |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_inclu_special_throttle | Integer               | Indicates whether an excluded request throttling configuration has been created.                                                                                                                                                                                            |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  1: yes                                                                                                                                                                                                                                                                   |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  2: no                                                                                                                                                                                                                                                                    |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | Enumeration values:                                                                                                                                                                                                                                                         |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **1**                                                                                                                                                                                                                                                                    |
   |                           |                       |                                                                                                                                                                                                                                                                             |
   |                           |                       | -  **2**                                                                                                                                                                                                                                                                    |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time               | String                | Creation time.                                                                                                                                                                                                                                                              |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_name                  | String                | Environment in which the request throttling policy takes effect.                                                                                                                                                                                                            |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bind_id                   | String                | Policy binding record ID.                                                                                                                                                                                                                                                   |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bind_time                 | String                | Time when the policy is bound to the API.                                                                                                                                                                                                                                   |
   +---------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
     "throttles" : [ {
       "id" : "3437448ad06f4e0c91a224183116e965",
       "name" : "throttle_demo",
       "api_call_limits" : 800,
       "user_call_limits" : 500,
       "app_call_limits" : 300,
       "ip_call_limits" : 600,
       "time_interval" : 1,
       "time_unit" : "SECOND",
       "create_time" : "2020-07-31T08:44:02Z",
       "remark" : "Total: 800 calls/second; user: 500 calls/second; app: 300 calls/second; IP address: 600 calls/second",
       "is_inclu_special_throttle" : 2,
       "env_name" : "RELEASE",
       "type" : 1,
       "bind_id" : "3e06ac135e18477e918060d3c59d6f6a",
       "bind_time" : "2020-08-03T12:25:52Z",
       "bind_num" : 0,
       "enable_adaptive_control" : "FALSE"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:throttle_name. Please refer to the support documentation"
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
     "error_code" : "APIG.3002",
     "error_msg" : "API 5f918d104dc84480a75166ba99efff21 does not exist"
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
