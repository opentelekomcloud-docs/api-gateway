:original_name: ListBackendInstancesV2.html

.. _ListBackendInstancesV2:

Querying Backend Servers of a VPC Channel
=========================================

Function
--------

This API is used to query the backend instances of a specified VPC channel.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/vpc-channels/{vpc_channel_id}/members

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                           |
   +================+===========+========+=======================================================================================================================+
   | project_id     | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id    | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | vpc_channel_id | Yes       | String | VPC channel ID.                                                                                                       |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                         |
   +===================+=================+=================+=====================================================================================================================================================================================+
   | offset            | No              | Long            | Offset from which the query starts. If the value is less than 0, it is automatically converted to 0.                                                                                |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Default: **0**                                                                                                                                                                      |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit             | No              | Integer         | Number of items displayed on each page. A value less than or equal to 0 will be automatically converted to 20, and a value greater than 500 will be automatically converted to 500. |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Minimum: **1**                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **500**                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Default: **20**                                                                                                                                                                     |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name              | No              | String          | Cloud server name.                                                                                                                                                                  |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_name | No              | String          | Backend server group name.                                                                                                                                                          |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_id   | No              | String          | Backend server group ID.                                                                                                                                                            |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | precise_search    | No              | String          | Parameter name for exact matching. Separate multiple parameter names with commas (,).                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Currently, name and member_group_name are supported.                                                                                                                                |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-----------+----------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                   | Description                                          |
   +===========+========================================================================================+======================================================+
   | size      | Integer                                                                                | Length of the returned resource list.                |
   +-----------+----------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                   | Number of resources that match the query conditions. |
   +-----------+----------------------------------------------------------------------------------------+------------------------------------------------------+
   | members   | Array of :ref:`VpcMemberInfo <listbackendinstancesv2__response_vpcmemberinfo>` objects | Cloud server list.                                   |
   +-----------+----------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listbackendinstancesv2__response_vpcmemberinfo:

.. table:: **Table 5** VpcMemberInfo

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================================+
   | host                  | String                | Backend server address.                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | This parameter is required when the member type is IP address.                                                                                                                      |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Maximum: **64**                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | weight                | Integer               | Weight.                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | The higher the weight is, the more requests a backend service will receive.                                                                                                         |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Minimum: **0**                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Maximum: **10000**                                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_backup             | Boolean               | Indicates whether the backend service is a standby node.                                                                                                                            |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | After you enable this function, the backend service serves as a standby node. It works only when all non-standby nodes are faulty.                                                  |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | This function is supported only when your gateway has been upgraded to the corresponding version. If your gateway does not support this function, contact technical support.        |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Default: **false**                                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_name     | String                | Backend server group name. The server group facilitates backend service address modification.                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | Integer               | Backend server status.                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | -  1: available                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | -  2: unavailable                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Enumeration values:                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | -  **1**                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | -  **2**                                                                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port                  | Integer               | Backend server port.                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Minimum: **0**                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Maximum: **65535**                                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ecs_id                | String                | Backend server ID.                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | This parameter is required if the backend instance type is ecs. The value can contain 1 to 64 characters, including letters, digits, hyphens (-), and underscores (_).              |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Maximum: **255**                                                                                                                                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ecs_name              | String                | Backend server name.                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | This parameter is required if the backend instance type is ecs. The value can contain 1 to 64 characters, including letters, digits, hyphens (-), underscores (_), and periods (.). |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | Maximum: **64**                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Backend server ID.                                                                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_channel_id        | String                | VPC channel ID.                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Time when the backend server is added to the VPC channel.                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_id       | String                | Backend server group ID.                                                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
     "total" : 2,
     "size" : 2,
     "members" : [ {
       "host" : "192.168.0.5",
       "weight" : 1,
       "is_backup" : false,
       "member_group_name" : "",
       "status" : 1,
       "port" : 22,
       "ecs_id" : "192.168.0.5",
       "ecs_name" : "192.168.0.5",
       "id" : "be63c6260a1043888187f84af39c9f0e",
       "vpc_channel_id" : "56a7d7358e1b42459c9d730d65b14e59",
       "create_time" : "2020-07-23T07:11:57Z",
       "member_group_id" : ""
     }, {
       "host" : "192.168.1.124",
       "weight" : 2,
       "is_backup" : false,
       "member_group_name" : "",
       "status" : 1,
       "port" : 22,
       "ecs_id" : "192.168.1.124",
       "ecs_name" : "192.168.1.124",
       "id" : "a57b13f1b89b417ca8acd76909e6df67",
       "vpc_channel_id" : "56a7d7358e1b42459c9d730d65b14e59",
       "create_time" : "2020-07-23T07:11:57Z",
       "member_group_id" : ""
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
