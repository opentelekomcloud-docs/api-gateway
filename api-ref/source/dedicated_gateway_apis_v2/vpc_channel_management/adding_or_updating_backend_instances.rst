:original_name: AddingBackendInstancesV2.html

.. _AddingBackendInstancesV2:

Adding or Updating Backend Instances
====================================

Function
--------

This API is used to add backend instances to a VPC channel.

If a backend instance with the specified address already exists, the instance information is updated. If the request body contains multiple backend instance definitions with the same address, the first definition is used.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/vpc-channels/{vpc_channel_id}/members

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

   +-----------+-----------+-----------------------------------------------------------------------------------+--------------------+
   | Parameter | Mandatory | Type                                                                              | Description        |
   +===========+===========+===================================================================================+====================+
   | members   | Yes       | Array of :ref:`MemberInfo <addingbackendinstancesv2__request_memberinfo>` objects | Backend instances. |
   +-----------+-----------+-----------------------------------------------------------------------------------+--------------------+

.. _addingbackendinstancesv2__request_memberinfo:

.. table:: **Table 4** MemberInfo

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                                                                                                         |
   +===================+=================+=================+=====================================================================================================================================================================================+
   | host              | No              | String          | Backend server address.                                                                                                                                                             |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | This parameter is required when the member type is IP address.                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **64**                                                                                                                                                                     |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | weight            | No              | Integer         | Weight.                                                                                                                                                                             |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | The higher the weight is, the more requests a backend service will receive.                                                                                                         |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Minimum: **0**                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **10000**                                                                                                                                                                  |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_backup         | No              | Boolean         | Indicates whether the backend service is a standby node.                                                                                                                            |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | After you enable this function, the backend service serves as a standby node. It works only when all non-standby nodes are faulty.                                                  |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | This function is supported only when your gateway has been upgraded to the corresponding version. If your gateway does not support this function, contact technical support.        |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Default: **false**                                                                                                                                                                  |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_name | No              | String          | Backend server group name. The server group facilitates backend service address modification.                                                                                       |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status            | No              | Integer         | Backend server status.                                                                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | -  1: available                                                                                                                                                                     |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | -  2: unavailable                                                                                                                                                                   |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Enumeration values:                                                                                                                                                                 |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | -  **1**                                                                                                                                                                            |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | -  **2**                                                                                                                                                                            |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | port              | No              | Integer         | Backend server port.                                                                                                                                                                |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Minimum: **0**                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **65535**                                                                                                                                                                  |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ecs_id            | No              | String          | Backend server ID.                                                                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | This parameter is required if the backend instance type is ecs. The value can contain 1 to 64 characters, including letters, digits, hyphens (-), and underscores (_).              |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **255**                                                                                                                                                                    |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ecs_name          | No              | String          | Backend server name.                                                                                                                                                                |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | This parameter is required if the backend instance type is ecs. The value can contain 1 to 64 characters, including letters, digits, hyphens (-), underscores (_), and periods (.). |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **64**                                                                                                                                                                     |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 5** Response body parameters

   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                     | Description                                          |
   +===========+==========================================================================================+======================================================+
   | size      | Integer                                                                                  | Length of the returned resource list.                |
   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                     | Number of resources that match the query conditions. |
   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+
   | members   | Array of :ref:`VpcMemberInfo <addingbackendinstancesv2__response_vpcmemberinfo>` objects | Cloud server list.                                   |
   +-----------+------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _addingbackendinstancesv2__response_vpcmemberinfo:

.. table:: **Table 6** VpcMemberInfo

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
   | id                    | String                | Backend instance ID.                                                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_channel_id        | String                | VPC channel ID.                                                                                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Time when the backend server is added to the VPC channel.                                                                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_id       | String                | Backend server group ID.                                                                                                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Adding a cloud server IP address to a VPC channel

   .. code-block::

      {
        "members" : [ {
          "host" : "192.168.2.25",
          "weight" : 1,
          "member_group_name" : "test"
        } ]
      }

-  Adding a cloud server name to a VPC channel

   .. code-block::

      {
        "members" : [ {
          "ecs_id" : "1082720c-3c15-409c-9ae3-4983ddfb6a9d",
          "ecs_name" : "APIGtest02",
          "weight" : 2
        } ]
      }

Example Responses
-----------------

**Status code: 201**

Created

-  Example 1

   .. code-block::

      {
        "total" : 1,
        "size" : 1,
        "members" : [ {
          "host" : "192.168.2.25",
          "weight" : 1,
          "is_backup" : false,
          "member_group_name" : "test",
          "status" : 1,
          "port" : 22,
          "ecs_id" : "3082720c-3c15-409c-9ae3-4983ddfb6a9d",
          "ecs_name" : "APIGtest",
          "id" : "683b6807cad54122a6777ad047a6178e",
          "vpc_channel_id" : "105c6902457144a4820dff8b1ad63331",
          "create_time" : "2020-07-23T09:13:24Z",
          "member_group_id" : "cf868f0224084710a1e188b7d3057c52"
        } ]
      }

-  Example 2

   .. code-block::

      {
        "total" : 2,
        "size" : 2,
        "members" : [ {
          "host" : "192.168.0.17",
          "weight" : 2,
          "is_backup" : false,
          "member_group_name" : "test02",
          "status" : 1,
          "port" : 22,
          "ecs_id" : "1082720c-3c15-409c-9ae3-4983ddfb6a9d",
          "ecs_name" : "APIGtest02",
          "id" : "5c868f0224084710a1e188b7d3057c52",
          "vpc_channel_id" : "105c6902457144a4820dff8b1ad63331",
          "create_time" : "2020-07-23T09:03:53Z",
          "member_group_id" : "df868f0224084710a1e188b7d3057c52"
        }, {
          "host" : "192.168.0.39",
          "weight" : 1,
          "is_backup" : false,
          "member_group_name" : "test01",
          "status" : 1,
          "port" : 22,
          "ecs_id" : "ebe1104f-1254-4ac6-8ed7-366bec84f36e",
          "ecs_name" : "APIGtest01",
          "id" : "33ac0e39d005492eb1f4683e66d1a0d1",
          "vpc_channel_id" : "105c6902457144a4820dff8b1ad63331",
          "create_time" : "2020-07-23T07:24:34Z",
          "member_group_id" : "ef868f0224084710a1e188b7d3057c42"
        } ]
      }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2004",
     "error_msg" : "The parameter value is outside the allowable range,parameterName:weight. Please refer to the support documentation"
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
201         Created
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
