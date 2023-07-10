:original_name: ListProjectCofigsV2.html

.. _ListProjectCofigsV2:

Querying Resource Configurations of a Gateway
=============================================

Function
--------

This API is used to query the resource configurations and usage of a gateway.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/project/configs

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

   +-----------+-----------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                  | Description                                          |
   +===========+=======================================================================+======================================================+
   | size      | Integer                                                               | Length of the returned resource list.                |
   +-----------+-----------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                  | Number of resources that match the query conditions. |
   +-----------+-----------------------------------------------------------------------+------------------------------------------------------+
   | configs   | Array of :ref:`Config <listprojectcofigsv2__response_config>` objects | Quota list.                                          |
   +-----------+-----------------------------------------------------------------------+------------------------------------------------------+

.. _listprojectcofigsv2__response_config:

.. table:: **Table 5** Config

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                     |
   +=======================+=======================+=================================================================================================================================+
   | config_id             | String                | Quota ID.                                                                                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | config_name           | String                | Quota name.                                                                                                                     |
   |                       |                       |                                                                                                                                 |
   |                       |                       | Enumeration values:                                                                                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_NUM_LIMIT**                                                                                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_NUM_LIMIT**                                                                                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APIGROUP_NUM_LIMIT**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **ENVIRONMENT_NUM_LIMIT**                                                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **VARIABLE_NUM_LIMIT**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **SIGN_NUM_LIMIT**                                                                                                           |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **THROTTLE_NUM_LIMIT**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APIGROUP_DOMAIN_NUM_LIMIT**                                                                                                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_VERSION_NUM_LIMIT**                                                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **VPC_NUM_LIMIT**                                                                                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **VPC_INSTANCE_NUM_LIMIT**                                                                                                   |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_PARAM_NUM_LIMIT**                                                                                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_USER_CALL_LIMIT**                                                                                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **ACL_NUM_LIMIT**                                                                                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_THROTTLE_LIMIT**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **USER_THROTTLE_LIMIT**                                                                                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_NUM_LIMIT_PER_GROUP**                                                                                                  |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_POLICY_NUM_LIMIT**                                                                                                     |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_CONDITION_NUM_LIMIT**                                                                                                  |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **SL_DOMAIN_CALL_LIMIT**                                                                                                     |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **ELB_SWITCH**                                                                                                               |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **AUTHORIZER_NUM_LIMIT**                                                                                                     |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **AUTHORIZER_IDENTITY_NUM_LIMIT**                                                                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_CODE_NUM_LIMIT**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **REGION_MANAGER_WHITELIST_SERVICES**                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_SWAGGER_NUM_LIMIT**                                                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_TAG_NUM_LIMIT**                                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **LTS_SWITCH**                                                                                                               |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_KEY_SECRET_SWITCH**                                                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **RESPONSE_NUM_LIMIT**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **CONFIG_NUM_LIMIT_PER_APP**                                                                                                 |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **BACKEND_TOKEN_ALLOW_SWITCH**                                                                                               |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_TOKEN_SWITCH**                                                                                                         |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **API_DESIGNER_SWITCH**                                                                                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_API_KEY_SWITCH**                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_BASIC_SWITCH**                                                                                                         |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_JWT_SWITCH**                                                                                                           |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_ROUTE_SWITCH**                                                                                                         |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **PUBLIC_KEY_SWITCH**                                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **APP_SECRET_SWITCH**                                                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **CASCADE_SWITCH**                                                                                                           |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  **IS_INIT_API_PATH_HASH**                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | config_value          | String                | Quota value.                                                                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | It indicates the value of the quota for the current gateway.                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | config_time           | String                | Time when the quota is created.                                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | remark                | String                | Quota description.                                                                                                              |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_NUM_LIMIT: Maximum number of APIs you can create.                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_NUM_LIMIT: Maximum number of apps you can create.                                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APIGROUP_NUM_LIMIT: Maximum number of API groups you can create.                                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  ENVIRONMENT_NUM_LIMIT: Maximum number of environments you can create.                                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  VARIABLE_NUM_LIMIT: Maximum number of environment variables you can create for an API group.                                 |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  SIGN_NUM_LIMIT: Maximum number of signature keys you can create.                                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  THROTTLE_NUM_LIMIT: Maximum number of request throttling policies you can create.                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APIGROUP_DOMAIN_NUM_LIMIT: Maximum number of custom domain names you can bind to an API group.                               |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_VERSION_NUM_LIMIT: Maximum number of versions you can retain for an API.                                                 |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  VPC_NUM_LIMIT: Maximum number of VPC channels you can create.                                                                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  VPC_INSTANCE_NUM_LIMIT: Maximum number of cloud servers you can associate with a VPC channel.                                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_PARAM_NUM_LIMIT: Maximum number of parameters you can configure for an API.                                              |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_USER_CALL_LIMIT: Maximum number of times an API can be called within a specific period.                                  |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  ACL_NUM_LIMIT: Maximum number of access control policies you can create.                                                     |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_THROTTLE_LIMIT: Maximum number of excluded apps allowed for a request throttling policy.                                 |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  USER_THROTTLE_LIMIT: Maximum number of excluded tenants allowed for a request throttling policy.                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_NUM_LIMIT_PER_GROUP: Maximum number of APIs you can create for an API group.                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_POLICY_NUM_LIMIT: Maximum number of policy backends you can configure for an API.                                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_CONDITION_NUM_LIMIT: Maximum number of conditions you can configure for a policy backend.                                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  SL_DOMAIN_CALL_LIMIT: Maximum number of requests that can be sent to a subdomain name within a specific period.              |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  ELB_SWITCH: Whether to enable ELB channels.                                                                                  |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  AUTHORIZER_NUM_LIMIT: Maximum number of custom authorizers you can create.                                                   |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  AUTHORIZER_IDENTITY_NUM_LIMIT: Maximum number of identity sources you can configure for a custom authorizer.                 |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_CODE_NUM_LIMIT: Maximum number of AppCodes you can create for an app.                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  REGION_MANAGER_WHITELIST_SERVICES: Whitelist of services that are not verified by the region manager.                        |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_SWAGGER_NUM_LIMIT: Maximum number of Swagger files you can bind to an API group.                                         |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_TAG_NUM_LIMIT: Maximum number of tags you can configure for an API.                                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  LTS_SWITCH: Whether to enable LTS log reporting.                                                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_KEY_SECRET_SWITCH: Whether to enable AppKey and AppSecret customization. 1: enable; 2: disable.                          |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  RESPONSE_NUM_LIMIT: Maximum number of responses you can create for an API group.                                             |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  CONFIG_NUM_LIMIT_PER_APP: Maximum number of configuration items you can set for an app.                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  BACKEND_TOKEN_ALLOW_SWITCH: Whether to allow tenants to transparently transmit tokens to the backend. 1: allow; 2: disallow. |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_TOKEN_SWITCH: Whether to enable AppTokens.                                                                               |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  API_DESIGNER_SWITCH: Whether to enable the API designer. 1: enable; 2: disable.                                              |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_API_KEY_SWITCH: Whether to enable APP_API_KEY authentication.                                                            |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_BASIC_SWITCH: Whether to enable APP_BASIC authentication.                                                                |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_JWT_SWITCH: Whether to enable APP_JWT authentication.                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_ROUTE_SWITCH: Whether to enable app routes.                                                                              |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  PUBLIC_KEY_SWITCH: Whether to enable PUBLIC_KEY backend authentication.                                                      |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  APP_SECRET_SWITCH: Whether to enable APP_SECRET authentication.                                                              |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  CASCADE_SWITCH: Whether to enable cascaded gateways.                                                                         |
   |                       |                       |                                                                                                                                 |
   |                       |                       | -  IS_INIT_API_PATH_HASH: Whether API path hashing has been performed.                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | used                  | Long                  | Used quota of the gateway.                                                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

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
     "total" : 43,
     "size" : 2,
     "configs" : [ {
       "config_id" : "9",
       "config_name" : "API_VERSION_NUM_LIMIT",
       "config_value" : "10",
       "config_time" : "2019-02-12T19:42:19.914989Z",
       "remark" : "xxx",
       "used" : 0
     }, {
       "config_id" : "8",
       "config_name" : "APIGROUP_DOMAIN_NUM_LIMIT",
       "config_value" : "5",
       "config_time" : "2019-02-12T19:42:19.914989Z",
       "remark" : "xxx",
       "used" : 0
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:instance_id. Please refer to the support documentation"
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
     "error_msg" : "The instance does not exist;id:eddc4d25480b4cd6b512f270a1b8b341"
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
