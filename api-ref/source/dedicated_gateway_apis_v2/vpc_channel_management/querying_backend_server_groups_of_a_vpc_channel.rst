:original_name: ListMemberGroups.html

.. _ListMemberGroups:

Querying Backend Server Groups of a VPC Channel
===============================================

Function
--------

This API is used to query backend server groups of a VPC channel.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/vpc-channels/{vpc_channel_id}/member-groups

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
   | dict_code         | No              | String          | Dictionary code.                                                                                                                                                                    |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | The value can contain letters, digits, hyphens (-), underscores (_), and periods (.).                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | This parameter is currently not supported.                                                                                                                                          |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Minimum: **3**                                                                                                                                                                      |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Maximum: **64**                                                                                                                                                                     |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_name | No              | String          | Backend server group name of the VPC channel.                                                                                                                                       |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | precise_search    | No              | String          | Parameter name for exact matching. Separate multiple parameter names with commas (,).                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | Currently, member_group_name is supported.                                                                                                                                          |
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

   +---------------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter     | Type                                                                                 | Description                                          |
   +===============+======================================================================================+======================================================+
   | size          | Integer                                                                              | Length of the returned resource list.                |
   +---------------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | total         | Long                                                                                 | Number of resources that match the query conditions. |
   +---------------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | member_groups | Array of :ref:`MemberGroupInfo <listmembergroups__response_membergroupinfo>` objects | Backend server groups of the VPC channel.            |
   +---------------+--------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listmembergroups__response_membergroupinfo:

.. table:: **Table 5** MemberGroupInfo

   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                     | Description                                                                                                                                                                                                                             |
   +=======================+==========================================================================================+=========================================================================================================================================================================================================================================+
   | member_group_name     | String                                                                                   | Name of the VPC channel's backend server group. It can contain 3 to 64 characters, starting with a letter. Only letters, digits, underscores (_), hyphens (-), and periods (.) are allowed.                                             |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_remark   | String                                                                                   | Description of the backend server group.                                                                                                                                                                                                |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Maximum: **255**                                                                                                                                                                                                                        |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_weight   | Integer                                                                                  | Weight of the backend server group.                                                                                                                                                                                                     |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | If the server group contains servers and a weight has been set for it, the weight is automatically used to assign weights to servers in this group.                                                                                     |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Minimum: **0**                                                                                                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Maximum: **100**                                                                                                                                                                                                                        |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dict_code             | String                                                                                   | Dictionary code of the backend server group.                                                                                                                                                                                            |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | The value can contain letters, digits, hyphens (-), underscores (_), and periods (.).                                                                                                                                                   |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Currently, this parameter is not supported.                                                                                                                                                                                             |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Minimum: **3**                                                                                                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Maximum: **64**                                                                                                                                                                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | microservice_version  | String                                                                                   | Version of the backend server group. This parameter is supported only when the VPC channel type is microservice.                                                                                                                        |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Maximum: **64**                                                                                                                                                                                                                         |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | microservice_port     | Integer                                                                                  | Port of the backend server group. This parameter is supported only when the VPC channel type is microservice. If the port number is 0, all addresses in the backend server group use the original load balancing port to inherit logic. |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Minimum: **0**                                                                                                                                                                                                                          |
   |                       |                                                                                          |                                                                                                                                                                                                                                         |
   |                       |                                                                                          | Maximum: **65535**                                                                                                                                                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | microservice_labels   | Array of :ref:`MicroserviceLabel <listmembergroups__response_microservicelabel>` objects | Tags of the backend server group. This parameter is supported only when the VPC channel type is microservice.                                                                                                                           |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | member_group_id       | String                                                                                   | ID of the backend server group of the VPC channel.                                                                                                                                                                                      |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                                                                                   | Time when the backend server group is created.                                                                                                                                                                                          |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                                                                                   | Time when the backend server group is updated.                                                                                                                                                                                          |
   +-----------------------+------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listmembergroups__response_microservicelabel:

.. table:: **Table 6** MicroserviceLabel

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                          |
   +=======================+=======================+======================================================================================================================================+
   | label_name            | String                | Tag name.                                                                                                                            |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Start and end with a letter or digit. Use only letters, digits, hyphens (-), underscores (_), and periods (.). (Max. 63 characters.) |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Minimum: **1**                                                                                                                       |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Maximum: **63**                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | label_value           | String                | Tag value.                                                                                                                           |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Start and end with a letter or digit. Use only letters, digits, hyphens (-), underscores (_), and periods (.). (Max. 63 characters.) |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Minimum: **1**                                                                                                                       |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Maximum: **63**                                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 1,
     "size" : 1,
     "member_groups" : [ {
       "member_group_name" : "vpc_member_group",
       "member_group_remark" : "remark",
       "member_group_weight" : 1,
       "dict_code" : "",
       "member_group_id" : "105c6902457144a4820dff8b1ad63331",
       "create_time" : "2020-07-23T07:24:33Z",
       "update_time" : "2020-07-23T07:24:33Z",
       "microservice_version" : "",
       "microservice_port" : 0,
       "microservice_labels" : [ ]
     } ]
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
     "error_code" : "APIG.3030",
     "error_msg" : "The instance does not exist,id:56a7d7358e1b42459c9d730d65b14e59"
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
