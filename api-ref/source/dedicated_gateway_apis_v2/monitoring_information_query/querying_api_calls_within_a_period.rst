:original_name: ListLatelyApiStatisticsV2_1.html

.. _ListLatelyApiStatisticsV2_1:

Querying API Calls Within a Period
==================================

Function
--------

This API is used to query the number of times APIs in an API group are called within a period. The query is based on 1 minute. If the time range is within one hour, the server returns the number of API calls made every minute.

.. note::

   For security purposes, clear your operation records, including but not limited to records in the ~/.bash_history and /var/log/messages directories (if any), after running the curl command on the server to query information.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/statistics/api/latest

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                  |
   +===========+===========+========+==============================================================================================================+
   | api_id    | Yes       | String | API ID.                                                                                                      |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------+
   | duration  | Yes       | String | Time range (unit: h or m). For example, 1h refers to the latest 1 hour and 1m refers to the latest 1 minute. |
   +-----------+-----------+--------+--------------------------------------------------------------------------------------------------------------+

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

   +------------+---------------------------------------------------------------------------------------------+------------------------------------+
   | Parameter  | Type                                                                                        | Description                        |
   +============+=============================================================================================+====================================+
   | code       | String                                                                                      | Response code.                     |
   +------------+---------------------------------------------------------------------------------------------+------------------------------------+
   | msg        | String                                                                                      | Response message.                  |
   +------------+---------------------------------------------------------------------------------------------+------------------------------------+
   | start_time | Long                                                                                        | Timestamp (UTC) of the start time. |
   +------------+---------------------------------------------------------------------------------------------+------------------------------------+
   | end_time   | Long                                                                                        | Timestamp (UTC) of the end time.   |
   +------------+---------------------------------------------------------------------------------------------+------------------------------------+
   | list       | Array of :ref:`StatisticsAPI <listlatelyapistatisticsv2_1__response_statisticsapi>` objects | Statistic data.                    |
   +------------+---------------------------------------------------------------------------------------------+------------------------------------+

.. _listlatelyapistatisticsv2_1__response_statisticsapi:

.. table:: **Table 5** StatisticsAPI

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
   | max_inner_latency     | Integer               | Maximum gateway latency.            |
   |                       |                       |                                     |
   |                       |                       | Unit: ms                            |
   +-----------------------+-----------------------+-------------------------------------+
   | avg_inner_latency     | Float                 | Average gateway latency.            |
   |                       |                       |                                     |
   |                       |                       | Unit: ms                            |
   +-----------------------+-----------------------+-------------------------------------+
   | max_backend_latency   | Integer               | Maximum backend latency.            |
   +-----------------------+-----------------------+-------------------------------------+
   | avg_backend_latency   | Float                 | Average backend latency.            |
   +-----------------------+-----------------------+-------------------------------------+
   | output_throughput     | Long                  | Downstream throughput (bytes).      |
   +-----------------------+-----------------------+-------------------------------------+
   | input_throughput      | Long                  | Upstream throughput (bytes).        |
   +-----------------------+-----------------------+-------------------------------------+
   | current_minute        | Long                  | Timestamp (UTC) of API access.      |
   +-----------------------+-----------------------+-------------------------------------+
   | cycle                 | String                | Statistical period.                 |
   |                       |                       |                                     |
   |                       |                       | Enumeration values:                 |
   |                       |                       |                                     |
   |                       |                       | -  **MINUTE**                       |
   |                       |                       |                                     |
   |                       |                       | -  **HOUR**                         |
   |                       |                       |                                     |
   |                       |                       | -  **DAY**                          |
   +-----------------------+-----------------------+-------------------------------------+
   | api_id                | String                | API ID.                             |
   +-----------------------+-----------------------+-------------------------------------+
   | group_id              | String                | API group ID.                       |
   +-----------------------+-----------------------+-------------------------------------+
   | provider              | String                | API provider.                       |
   +-----------------------+-----------------------+-------------------------------------+
   | req_time              | String                | Request time.                       |
   +-----------------------+-----------------------+-------------------------------------+
   | register_time         | String                | Recording time.                     |
   +-----------------------+-----------------------+-------------------------------------+
   | status                | Integer               | Status.                             |
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
     "start_time" : 1595573280,
     "end_time" : 1595576820,
     "list" : [ {
       "api_id" : "39bce6d25a3f470e8cf7b2c97174f7d9",
       "avg_backend_latency" : 2.71,
       "avg_inner_latency" : 1.57,
       "avg_latency" : 4.14,
       "current_minute" : 1595576640,
       "cycle" : "MINUTE",
       "group_id" : "d0fc4e40b7d1492cba802f667c7c7226",
       "input_throughput" : 1071,
       "max_backend_latency" : 6,
       "max_inner_latency" : 8,
       "max_latency" : 14,
       "output_throughput" : 3790,
       "provider" : "73d69ae0cfcf460190522d06b60f05ad",
       "register_time" : "2020-07-24 15:44:56",
       "req_count" : 7,
       "req_count2xx" : 0,
       "req_count4xx" : 6,
       "req_count5xx" : 1,
       "req_count_error" : 7,
       "req_time" : "2020-07-24 15:44:00",
       "status" : 1
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:api_id. Please refer to the support documentation"
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
     "error_msg" : "API 39bce6d25a3f470e8cf7b2c97174f7d9 does not exist"
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
