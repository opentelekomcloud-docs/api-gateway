:original_name: ListMetricData.html

.. _ListMetricData:

Querying Monitoring Data
========================

Function
--------

This API is used to query the monitoring metric data at a specified granularity in a specified period of time.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/metric-data

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                    |
   +=================+=================+=================+================================================================================================================================================+
   | dim             | Yes             | String          | Metric dimension.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  inbound_eip: Inbound public network bandwidth, which is supported only by gateways that support load balancing.                             |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  outbound_eip: Outbound public network bandwidth.                                                                                            |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | Enumeration values:                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **inbound_eip**                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **outbound_eip**                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | metric_name     | Yes             | String          | Metric name.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  upstream_bandwidth: Outbound bandwidth.                                                                                                     |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  downstream_bandwidth: Inbound bandwidth.                                                                                                    |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  upstream_bandwidth_usage: Outbound bandwidth usage.                                                                                         |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  downstream_bandwidth_usage: Inbound bandwidth usage.                                                                                        |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  up_stream: Outbound traffic.                                                                                                                |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  down_stream: Inbound traffic.                                                                                                               |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | Enumeration values:                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **upstream_bandwidth**                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **downstream_bandwidth**                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **upstream_bandwidth_usage**                                                                                                                |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **downstream_bandwidth_usage**                                                                                                              |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **up_stream**                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **down_stream**                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | from            | Yes             | String          | Start time of the query. The time is a UNIX timestamp and the unit is ms.                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | to              | Yes             | String          | End time of the query. The time is a UNIX timestamp and the unit is ms. The value of parameter from must be earlier than that of parameter to. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | period          | Yes             | Integer         | Monitoring data granularity.                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  1: Real-time data.                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  300: 5 minutes.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  1200: 20 minutes.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  3600: 1 hour.                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  14400: 4 hours.                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  86400: 1 day.                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | Enumeration values:                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **1**                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **300**                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **1200**                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **3600**                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **14400**                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **86400**                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | filter          | Yes             | String          | Data rollup mode.                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  average: Average value of the metric data in the rollup period.                                                                             |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  max: Maximum value of the metric data in the rollup period.                                                                                 |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  min: Minimum value of the metric data in the rollup period.                                                                                 |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  sum: Sum of the metric data in the rollup period.                                                                                           |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  variance: Variance value of the metric data in the rollup period.                                                                           |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | Enumeration values:                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **average**                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **max**                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **min**                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **sum**                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                |
   |                 |                 |                 | -  **variance**                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +------------+--------------------------------------------------------------------------+--------------+
   | Parameter  | Type                                                                     | Description  |
   +============+==========================================================================+==============+
   | datapoints | Array of :ref:`MetricData <listmetricdata__response_metricdata>` objects | Metric data. |
   +------------+--------------------------------------------------------------------------+--------------+

.. _listmetricdata__response_metricdata:

.. table:: **Table 5** MetricData

   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                                                                                                 |
   +===========+=========+=============================================================================================================================================+
   | average   | Integer | Average value of metric data within a rollup period. This parameter is supported only when the value of filter in the request is average.   |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | max       | Integer | Maximum value of metric data within a rollup period. This parameter is supported only when the value of filter in the request is max.       |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | min       | Integer | Minimum value of metric data within a rollup period. This parameter is supported only when the value of filter in the request is min.       |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | sum       | Integer | Sum of metric data within a rollup period. This parameter is supported only when the value of filter in the request is sum.                 |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | variance  | Integer | Variance value of metric data within a rollup period. This parameter is supported only when the value of filter in the request is variance. |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | timestamp | Long    | Time when the metric is collected. It is a UNIX timestamp in milliseconds.                                                                  |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | unit      | String  | Metric unit.                                                                                                                                |
   +-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+

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
     "datapoints" : [ {
       "average" : 5,
       "timestamp" : 1665304920000,
       "unit" : "Byte"
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
