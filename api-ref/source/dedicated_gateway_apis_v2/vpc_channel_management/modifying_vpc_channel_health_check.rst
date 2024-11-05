:original_name: UpdateHealthCheck.html

.. _UpdateHealthCheck:

Modifying VPC Channel Health Check
==================================

Function
--------

This API is used to modify the health check configuration of a VPC channel.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/vpc-channels/{vpc_channel_id}/health-config

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                             |
   +================+===========+========+=========================================================================================================+
   | project_id     | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id    | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | vpc_channel_id | Yes       | String | VPC channel ID.                                                                                         |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                             |
   +====================+=================+=================+=========================================================================================================================================================================================+
   | protocol           | Yes             | String          | Protocol for performing health checks on backend servers in the VPC channel.                                                                                                            |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  TCP                                                                                                                                                                                  |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  HTTP                                                                                                                                                                                 |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  HTTPS                                                                                                                                                                                |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Enumeration values:                                                                                                                                                                     |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **TCP**                                                                                                                                                                              |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **HTTP**                                                                                                                                                                             |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **HTTPS**                                                                                                                                                                            |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | path               | No              | String          | Destination path for health checks. This parameter is required if protocol is set to http or https.                                                                                     |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | method             | No              | String          | Request method for health checks.                                                                                                                                                       |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Default: **GET**                                                                                                                                                                        |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Enumeration values:                                                                                                                                                                     |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **GET**                                                                                                                                                                              |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **HEAD**                                                                                                                                                                             |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port               | No              | Integer         | Destination port for health checks. If this parameter is not specified or set to 0, the host port of the VPC channel is used.                                                           |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | If this parameter is set to a non-zero value, the corresponding port is used for health checks.                                                                                         |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Minimum: **0**                                                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Maximum: **65535**                                                                                                                                                                      |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | threshold_normal   | Yes             | Integer         | Healthy threshold. It refers to the number of consecutive successful checks required for a backend server to be considered healthy.                                                     |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Minimum: **1**                                                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Maximum: **10**                                                                                                                                                                         |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | threshold_abnormal | Yes             | Integer         | Unhealthy threshold, which refers to the number of consecutive failed checks required for a backend server to be considered unhealthy.                                                  |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Minimum: **1**                                                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Maximum: **10**                                                                                                                                                                         |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_interval      | Yes             | Integer         | Interval between consecutive checks. Unit: s. The value must be greater than the value of timeout.                                                                                      |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Minimum: **1**                                                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Maximum: **300**                                                                                                                                                                        |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | http_code          | No              | String          | Response codes for determining a successful HTTP response. The value can be any integer within 100-599 in one of the following formats:                                                 |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  Multiple values, for example, 200,201,202                                                                                                                                            |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  Range, for example, 200-299                                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  Multiple values and ranges, for example, 201,202,210-299. This parameter is required if protocol is set to http.                                                                     |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_client_ssl  | No              | Boolean         | Indicates whether to enable two-way authentication. If this function is enabled, the certificate specified in the backend_client_certificate configuration item of the gateway is used. |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Default: **false**                                                                                                                                                                      |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status             | No              | Integer         | Health check result.                                                                                                                                                                    |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  1: available                                                                                                                                                                         |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  2: unavailable                                                                                                                                                                       |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Enumeration values:                                                                                                                                                                     |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **1**                                                                                                                                                                                |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | -  **2**                                                                                                                                                                                |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timeout            | Yes             | Integer         | Timeout for determining whether a health check fails. Unit: s. The value must be less than the value of time_interval.                                                                  |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Minimum: **1**                                                                                                                                                                          |
   |                    |                 |                 |                                                                                                                                                                                         |
   |                    |                 |                 | Maximum: **30**                                                                                                                                                                         |
   +--------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================+
   | protocol              | String                | Protocol for performing health checks on backend servers in the VPC channel.                                                                                                            |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  TCP                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  HTTP                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  HTTPS                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Enumeration values:                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **TCP**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **HTTP**                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **HTTPS**                                                                                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | path                  | String                | Destination path for health checks. This parameter is required if protocol is set to http or https.                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | method                | String                | Request method for health checks.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Default: **GET**                                                                                                                                                                        |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Enumeration values:                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **GET**                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **HEAD**                                                                                                                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port                  | Integer               | Destination port for health checks. If this parameter is not specified or set to 0, the host port of the VPC channel is used.                                                           |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | If this parameter is set to a non-zero value, the corresponding port is used for health checks.                                                                                         |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Minimum: **0**                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Maximum: **65535**                                                                                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | threshold_normal      | Integer               | Healthy threshold. It refers to the number of consecutive successful checks required for a backend server to be considered healthy.                                                     |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Minimum: **1**                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Maximum: **10**                                                                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | threshold_abnormal    | Integer               | Unhealthy threshold, which refers to the number of consecutive failed checks required for a backend server to be considered unhealthy.                                                  |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Minimum: **1**                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Maximum: **10**                                                                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_interval         | Integer               | Interval between consecutive checks. Unit: s. The value must be greater than the value of timeout.                                                                                      |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Minimum: **1**                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Maximum: **300**                                                                                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | http_code             | String                | Response codes for determining a successful HTTP response. The value can be any integer within 100-599 in one of the following formats:                                                 |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  Multiple values, for example, 200,201,202                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  Range, for example, 200-299                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  Multiple values and ranges, for example, 201,202,210-299. This parameter is required if protocol is set to http.                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enable_client_ssl     | Boolean               | Indicates whether to enable two-way authentication. If this function is enabled, the certificate specified in the backend_client_certificate configuration item of the gateway is used. |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Default: **false**                                                                                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Health check result.                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  1: available                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  2: unavailable                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Enumeration values:                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **1**                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | -  **2**                                                                                                                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timeout               | Integer               | Timeout for determining whether a health check fails. Unit: s. The value must be less than the value of time_interval.                                                                  |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Minimum: **1**                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | Maximum: **30**                                                                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_channel_id        | String                | VPC channel ID.                                                                                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Health check ID.                                                                                                                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

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

Modifying health check configurations of a VPC channel

.. code-block::

   {
     "http_code" : "200",
     "path" : "/vpc/demo",
     "port" : 22,
     "protocol" : "http",
     "threshold_abnormal" : 5,
     "threshold_normal" : 2,
     "time_interval" : 10,
     "timeout" : 5,
     "enable_client_ssl" : false
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "protocol" : "http",
     "path" : "/vpc/demo",
     "method" : "GET",
     "port" : 22,
     "threshold_abnormal" : 5,
     "threshold_normal" : 2,
     "time_interval" : 10,
     "http_code" : "200",
     "enable_client_ssl" : false,
     "status" : 1,
     "timeout" : 5,
     "id" : "3b3d02026c5f402d85e8645ea95b0816",
     "vpc_channel_id" : "d38c55c926ca44c2bfb37886d93b9a0d",
     "create_time" : "2020-07-23T07:11:57Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2001",
     "error_msg" : "The request parameters must be specified, parameter name:members"
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
     "error_code" : "APIG.3023",
     "error_msg" : "The VPC channel does not exist,id:56a7d7358e1b42459c9d730d65b14e59"
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
