:original_name: ListRequestThrottlingPolicyV2.html

.. _ListRequestThrottlingPolicyV2:

Querying Request Throttling Policies
====================================

Function
--------

This API is used to query all the request throttling policies.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/throttles

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
   | id              | No              | String          | Request throttling policy ID.                                                                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Request throttling policy name.                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | precise_search  | No              | String          | Parameter name (name) for exact matching.                                                                                                                                           |
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

   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                          | Description                                          |
   +===========+===============================================================================================+======================================================+
   | size      | Integer                                                                                       | Length of the returned resource list.                |
   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                          | Number of resources that match the query conditions. |
   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | throttles | Array of :ref:`ThrottlesInfo <listrequestthrottlingpolicyv2__response_throttlesinfo>` objects | Request throttling policy list.                      |
   +-----------+-----------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listrequestthrottlingpolicyv2__response_throttlesinfo:

.. table:: **Table 5** ThrottlesInfo

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
     "throttles" : [ {
       "name" : "throttle_demo",
       "create_time" : "2020-07-31T08:44:02.205366118Z",
       "remark" : "Total: 800 calls/second; user: 500 calls/second; app: 300 calls/second; IP address: 600 calls/second",
       "type" : 1,
       "time_interval" : 1,
       "ip_call_limits" : 600,
       "app_call_limits" : 300,
       "time_unit" : "SECOND",
       "api_call_limits" : 800,
       "id" : "3437448ad06f4e0c91a224183116e965",
       "user_call_limits" : 500,
       "enable_adaptive_control" : "FALSE",
       "bind_num" : 0,
       "is_inclu_special_throttle" : 2
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:name. Please refer to the support documentation"
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
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
