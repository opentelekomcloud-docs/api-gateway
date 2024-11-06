:original_name: CreateInstanceV2.html

.. _CreateInstanceV2:

Creating a Dedicated Gateway (Pay-Per-Use)
==========================================

Function
--------

This API is used to create a pay-per-use dedicated gateway.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                       | Mandatory       | Type                                                                        | Description                                                                                                                                                                                                                                                                   |
   +=================================+=================+=============================================================================+===============================================================================================================================================================================================================================================================================+
   | description                     | No              | String                                                                      | Gateway description. The value can contain up to 255 characters except > and <.                                                                                                                                                                                               |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | maintain_begin                  | No              | String                                                                      | Start time of the maintenance time window. It must be in the format "xx:00:00". The value of xx can be 02, 06, 10, 14, 18, or 22.                                                                                                                                             |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | During the maintenance time period, O&M personnel perform maintenance on the gateway. During this period, services can still be used, but occasionally there may be temporary interruptions. Scheduled maintenance occurs infrequently (typically once every several months). |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | maintain_end                    | No              | String                                                                      | End time of the maintenance time window. It must be in the format "xx:00:00". There is a 4-hour difference between the start time and end time.                                                                                                                               |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | During the maintenance time period, O&M personnel perform maintenance on the gateway. During this period, services can still be used, but occasionally there may be temporary interruptions. Scheduled maintenance occurs infrequently (typically once every several months). |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_name                   | Yes             | String                                                                      | Gateway name.                                                                                                                                                                                                                                                                 |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Enter 3 to 64 characters, starting with a letter. Only letters, digits, hyphens (-), and underscores (_) are allowed.                                                                                                                                                         |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Minimum: **3**                                                                                                                                                                                                                                                                |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Maximum: **64**                                                                                                                                                                                                                                                               |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id                     | No              | String                                                                      | Gateway ID, which will be automatically generated if you do not specify this parameter.                                                                                                                                                                                       |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | spec_id                         | Yes             | String                                                                      | Gateway edition. Options:                                                                                                                                                                                                                                                     |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  BASIC                                                                                                                                                                                                                                                                      |
   |                                 |                 |                                                                             | -  PROFESSIONAL                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  ENTERPRISE                                                                                                                                                                                                                                                                 |
   |                                 |                 |                                                                             | -  PLATINUM                                                                                                                                                                                                                                                                   |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Platinum 2-8 are available only in certain regions.                                                                                                                                                                                                                           |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Enumeration values:                                                                                                                                                                                                                                                           |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  **BASIC**                                                                                                                                                                                                                                                                  |
   |                                 |                 |                                                                             | -  **PROFESSIONAL**                                                                                                                                                                                                                                                           |
   |                                 |                 |                                                                             | -  **ENTERPRISE**                                                                                                                                                                                                                                                             |
   |                                 |                 |                                                                             | -  **PLATINUM**                                                                                                                                                                                                                                                               |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpc_id                          | Yes             | String                                                                      | VPC ID.                                                                                                                                                                                                                                                                       |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | You can obtain it in either of the following ways:                                                                                                                                                                                                                            |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  Method 1: Log in to the VPC console, and click the name of a VPC to view the VPC ID on the displayed details page.                                                                                                                                                         |
   |                                 |                 |                                                                             | -  Method 2: Call the corresponding VPC API. For details, see section "Querying VPCs" in the VPC API Reference.                                                                                                                                                               |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | subnet_id                       | Yes             | String                                                                      | Subnet network ID.                                                                                                                                                                                                                                                            |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | You can obtain it in either of the following ways:                                                                                                                                                                                                                            |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  Method 1: Log in to the VPC console and click the target subnet on the Subnets page. You can view the network ID on the displayed page.                                                                                                                                    |
   |                                 |                 |                                                                             | -  Method 2: Call the corresponding VPC API. For details, see section "Querying Subnets" in the VPC API Reference.                                                                                                                                                            |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_group_id               | Yes             | String                                                                      | ID of the security group to which the gateway belongs.                                                                                                                                                                                                                        |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | You can obtain it in either of the following ways:                                                                                                                                                                                                                            |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  Method 1: Log in to the VPC console. Choose Access Control > Security Groups in the navigation pane. On the Security Groups page, click the target security group. Then view the security group ID on the displayed page.                                                  |
   |                                 |                 |                                                                             | -  Method 2: Call the corresponding VPC API. For details, see section "Querying Security Groups" in the VPC API Reference.                                                                                                                                                    |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | eip_id                          | No              | String                                                                      | EIP ID.                                                                                                                                                                                                                                                                       |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | After you bind an EIP to the gateway, users can access APIs in the gateway from public networks using the EIP.                                                                                                                                                                |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | To obtain an EIP ID, log in to the VPC console, and choose "Elastic IP and Bandwidth" > "EIPs" in the navigation pane. Click the name of the target EIP, and view the EIP ID on the displayed page.                                                                           |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | enterprise_project_id           | No              | String                                                                      | Enterprise project ID. This parameter is required for an enterprise account.                                                                                                                                                                                                  |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | You can obtain it in either of the following ways:                                                                                                                                                                                                                            |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  Method 1: Log in to the Enterprise Project Management page, click the name of the target enterprise project, and view the project ID on the displayed page.                                                                                                                |
   |                                 |                 |                                                                             | -  Method 2: Call the corresponding project management API. For details, see section "Querying the Enterprise Project List" in the Enterprise Management API Reference.                                                                                                       |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | available_zone_ids              | Yes             | Array of strings                                                            | AZs.                                                                                                                                                                                                                                                                          |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | An AZ is a physical region where resources use independent power supply and networks. AZs are physically isolated but interconnected through an internal network. To enhance application availability, create gateways in different AZs.                                      |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | To obtain AZ information, call the API used to query AZs.                                                                                                                                                                                                                     |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bandwidth_size                  | No              | Integer                                                                     | Outbound access bandwidth.                                                                                                                                                                                                                                                    |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | This parameter is required if public outbound access is enabled for the gateway. After you configure the bandwidth for the gateway, users can access resources on public networks. The minimum value is 5.                                                                    |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Default: **5**                                                                                                                                                                                                                                                                |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bandwidth_charging_mode         | No              | String                                                                      | Billing type of the public outbound access bandwidth. This parameter is required if public outbound access is enabled for the gateway.                                                                                                                                        |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  bandwidth: billed by bandwidth                                                                                                                                                                                                                                             |
   |                                 |                 |                                                                             | -  ipv6_enable: not supported currently                                                                                                                                                                                                                                       |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Default: **bandwidth**                                                                                                                                                                                                                                                        |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Enumeration values:                                                                                                                                                                                                                                                           |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  **bandwidth**                                                                                                                                                                                                                                                              |
   |                                 |                 |                                                                             | -  **ipv6_enable**                                                                                                                                                                                                                                                            |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | loadbalancer_provider           | No              | String                                                                      | Type of the load balancer used by the gateway.                                                                                                                                                                                                                                |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  elb: Elastic Load Balancer (available only in certain regions)                                                                                                                                                                                                             |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Enumeration values:                                                                                                                                                                                                                                                           |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  **elb**                                                                                                                                                                                                                                                                    |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                            | No              | Array of :ref:`TmsKeyValue <createinstancev2__request_tmskeyvalue>` objects | Tags.                                                                                                                                                                                                                                                                         |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | A maximum of 20 tags can be created for a gateway.                                                                                                                                                                                                                            |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Array Length: **0 - 20**                                                                                                                                                                                                                                                      |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | vpcep_service_name              | No              | String                                                                      | Name of a VPC endpoint service.                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | It can contain max. 16 characters, including letters, digits, hyphens (-), and underscores.                                                                                                                                                                                   |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | If this parameter is not specified, the system automatically generates a name in the "{region}.apig.{service_id}" format.                                                                                                                                                     |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | If this parameter is specified, the system automatically generates a name in the "{region}.{vpcep_service_name}.{service_id}" format.                                                                                                                                         |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | After the gateway is created, you can modify this name on the Gateways > VPC Endpoints page.                                                                                                                                                                                  |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ingress_bandwidth_size          | No              | Integer                                                                     | Public inbound access bandwidth.                                                                                                                                                                                                                                              |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | This parameter is required if public inbound access is enabled for the gateway and loadbalancer_provider is set to elb. After you bind an EIP to the gateway, users can access APIs in the gateway from public networks using the EIP. The minimum value is 5.                |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Default: **5**                                                                                                                                                                                                                                                                |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ingress_bandwidth_charging_mode | No              | String                                                                      | Billing type of the public inbound access bandwidth. This parameter is required if public inbound access is enabled for the gateway and loadbalancer_provider is set to elb.                                                                                                  |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  bandwidth: billed by bandwidth                                                                                                                                                                                                                                             |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Default: **bandwidth**                                                                                                                                                                                                                                                        |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | Enumeration values:                                                                                                                                                                                                                                                           |
   |                                 |                 |                                                                             |                                                                                                                                                                                                                                                                               |
   |                                 |                 |                                                                             | -  **bandwidth**                                                                                                                                                                                                                                                              |
   +---------------------------------+-----------------+-----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _createinstancev2__request_tmskeyvalue:

.. table:: **Table 4** TmsKeyValue

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                           |
   +=================+=================+=================+=======================================================================================================+
   | key             | No              | String          | Key.                                                                                                  |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Include UTF-8 letters, digits, spaces, or special characters ``(_.:=+-@).``                           |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Do not start with \_sys\_ because it is a system label.                                               |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Minimum: **1**                                                                                        |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Maximum: **128**                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Value.                                                                                                |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | You can enter letters, digits, and spaces or other special characters ``(_.:/=+-@)`` in UTF-8 format. |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Minimum: **0**                                                                                        |
   |                 |                 |                 |                                                                                                       |
   |                 |                 |                 | Maximum: **255**                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameters

   =========== ====== ============================================
   Parameter   Type   Description
   =========== ====== ============================================
   instance_id String Gateway ID.
   message     String Information about the gateway creation task.
   job_id      String Task ID.
   =========== ====== ============================================

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

Creating a gateway with network and security group configurations

.. code-block::

   {
     "available_zone_ids" : [ "xx-xxx-7b", "xx-xxx-7a" ],
     "bandwidth_size" : 5,
     "description" : "test create instance",
     "eip_id" : "41f961ab-2bdd-4ca7-9b59-cfc4fcef10c9",
     "enterprise_project_id" : "0",
     "instance_name" : "apig-demo",
     "maintain_begin" : "22:00:00",
     "maintain_end" : "02:00:00",
     "security_group_id" : "36d0ec18-bd10-4da7-86f3-ad7a5ddc55d7",
     "spec_id" : "PROFESSIONAL",
     "subnet_id" : "a938121c-11c4-4c91-b983-bc9acd347bb5",
     "vpc_id" : "0957108c-257c-4ce0-9e93-527d279ce763"
   }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "instance_id" : "6a7d71827fd54572b1f31aa9548fcc81",
     "message" : "JOB_ASSIGNED_FOR_PROVISIONING_0003I:The job JOB-bdb370eb6f4c4c73b61b95a9da38beb5 has been assigned to the instance 6a7d71827fd54572b1f31aa9548fcc81 for running provisioning.",
     "job_id" : "JOB-edbac2355fb7433e98f173ea2e452e2d"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIC.7211",
     "error_msg" : "Parameter value does not match the rules, parameter name[maintainBegin]"
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "APIC.7102",
     "error_msg" : "Incorrect token or token resolution failed"
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "APIC.7106",
     "error_msg" : "No permissions to request for the method"
   }

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "APIC.7301",
     "error_msg" : "Instance spec not found"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIC.9000",
     "error_msg" : "Failed to request internal service"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
202         Accepted
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
