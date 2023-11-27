:original_name: ListLatelyGroupStatisticsV2_1.html

.. _ListLatelyGroupStatisticsV2_1:

Querying API Calls Under an API Group in the Last One Hour
==========================================================

Function
--------

This API is used to query the total number of times all APIs in an API group are called based on the API group ID. The query is based on 1 minute. If the time range is within one hour, the server returns the number of API calls made every minute.

.. note::

   For security purposes, clear your operation records, including but not limited to records in the ~/.bash_history and /var/log/messages directories (if any), after running the curl command on the server to query information.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/statistics/group/latest

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ====== =============
   Parameter Mandatory Type   Description
   ========= ========= ====== =============
   group_id  Yes       String API group ID.
   ========= ========= ====== =============

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

   +------------+---------------------------------------------------------------------------------------------------+------------------------------------+
   | Parameter  | Type                                                                                              | Description                        |
   +============+===================================================================================================+====================================+
   | code       | String                                                                                            | Response code.                     |
   +------------+---------------------------------------------------------------------------------------------------+------------------------------------+
   | msg        | String                                                                                            | Response message.                  |
   +------------+---------------------------------------------------------------------------------------------------+------------------------------------+
   | start_time | Long                                                                                              | Timestamp (UTC) of the start time. |
   +------------+---------------------------------------------------------------------------------------------------+------------------------------------+
   | end_time   | Long                                                                                              | Timestamp (UTC) of the end time.   |
   +------------+---------------------------------------------------------------------------------------------------+------------------------------------+
   | list       | Array of :ref:`StatisticsGroup <listlatelygroupstatisticsv2_1__response_statisticsgroup>` objects | Statistic data.                    |
   +------------+---------------------------------------------------------------------------------------------------+------------------------------------+

.. _listlatelygroupstatisticsv2_1__response_statisticsgroup:

.. table:: **Table 5** StatisticsGroup

   +-----------------------+-----------------------+-------------------------------------+
   | Parameter             | Type                  | Description                         |
   +=======================+=======================+=====================================+
   | max_latency           | Integer               | Maximum latency.                    |
   |                       |                       |                                     |
   |                       |                       | Unit: ms                            |
   +-----------------------+-----------------------+-------------------------------------+
   | avg_latency           | Float                 | Average latency.                    |
   |                       |                       |                                     |
   |                       |                       | Unit: ms                            |
   +-----------------------+-----------------------+-------------------------------------+
   | req_count             | Integer               | Total number of requests.           |
   +-----------------------+-----------------------+-------------------------------------+
   | req_count2xx          | Integer               | Total number of 2xx response codes. |
   +-----------------------+-----------------------+-------------------------------------+
   | req_count4xx          | Integer               | Total number of 4xx response codes. |
   +-----------------------+-----------------------+-------------------------------------+
   | req_count5xx          | Integer               | Total number of 5xx response codes. |
   +-----------------------+-----------------------+-------------------------------------+
   | req_count_error       | Integer               | Errors.                             |
   +-----------------------+-----------------------+-------------------------------------+
   | output_throughput     | Long                  | Downstream throughput (bytes).      |
   +-----------------------+-----------------------+-------------------------------------+
   | input_throughput      | Long                  | Upstream throughput (bytes).        |
   +-----------------------+-----------------------+-------------------------------------+
   | current_minute        | Long                  | Timestamp (UTC) of API access.      |
   +-----------------------+-----------------------+-------------------------------------+
   | group_id              | String                | API group ID.                       |
   +-----------------------+-----------------------+-------------------------------------+
   | provider              | String                | API provider.                       |
   +-----------------------+-----------------------+-------------------------------------+
   | req_time              | String                | Request time.                       |
   +-----------------------+-----------------------+-------------------------------------+
   | register_time         | String                | Recording time.                     |
   +-----------------------+-----------------------+-------------------------------------+

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
     "code" : "APIG.0000",
     "start_time" : 1595574540,
     "end_time" : 1595578080,
     "list" : [ {
       "avg_latency" : 4.14,
       "current_minute" : 1595576640,
       "group_id" : "d0fc4e40b7d1492cba802f667c7c7226",
       "input_throughput" : 1071,
       "max_latency" : 14,
       "output_throughput" : 3790,
       "provider" : "73d69ae0cfcf460190522d06b60f05ad",
       "register_time" : "2020-07-24 15:44:56",
       "req_count" : 7,
       "req_count2xx" : 0,
       "req_count4xx" : 6,
       "req_count5xx" : 1,
       "req_count_error" : 7,
       "req_time" : "2020-07-24 15:44:00"
     }, {
       "avg_latency" : 3.67,
       "current_minute" : 1595577900,
       "group_id" : "d0fc4e40b7d1492cba802f667c7c7226",
       "input_throughput" : 915,
       "max_latency" : 6,
       "output_throughput" : 2763,
       "provider" : "73d69ae0cfcf460190522d06b60f05ad",
       "register_time" : "2020-07-24 16:05:12",
       "req_count" : 6,
       "req_count2xx" : 3,
       "req_count4xx" : 0,
       "req_count5xx" : 3,
       "req_count_error" : 3,
       "req_time" : "2020-07-24 16:05:00"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:group_id. Please refer to the support documentation"
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
     "error_code" : "APIG.3001",
     "error_msg" : "API group d0fc4e40b7d1492cba802f667c7c7226 does not exist"
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
