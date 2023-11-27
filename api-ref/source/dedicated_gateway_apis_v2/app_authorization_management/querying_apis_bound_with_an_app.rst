:original_name: ListApisBindedToAppV2_1.html

.. _ListApisBindedToAppV2_1:

Querying APIs Bound with an App
===============================

Function
--------

This API is used to query the APIs to which a specified app has been bound.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/app-auths/binded-apis

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
   | app_id          | Yes             | String          | App ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_id          | No              | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_name        | No              | String          | API name.                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | No              | String          | API group ID.                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_name      | No              | String          | API group name.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | No              | String          | ID of the environment in which the app has been authorized.                                                                                                                         |
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

   +-----------+-------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                | Description                                          |
   +===========+=====================================================================================+======================================================+
   | size      | Integer                                                                             | Length of the returned resource list.                |
   +-----------+-------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                | Number of resources that match the query conditions. |
   +-----------+-------------------------------------------------------------------------------------+------------------------------------------------------+
   | auths     | Array of :ref:`ApiAuthInfo <listapisbindedtoappv2_1__response_apiauthinfo>` objects | API list.                                            |
   +-----------+-------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listapisbindedtoappv2_1__response_apiauthinfo:

.. table:: **Table 5** ApiAuthInfo

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                           |
   +=======================+=======================+=======================================================================================+
   | id                    | String                | Authorization record ID.                                                              |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | api_id                | String                | API ID.                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | api_name              | String                | API name.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | group_name            | String                | Name of the API group to which the API belongs.                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | api_type              | Integer               | API type.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | api_remark            | String                | API description.                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | env_id                | String                | ID of the environment in which an app has been authorized to call the API.            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | auth_role             | String                | Authorizer.                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | auth_time             | String                | Authorization time.                                                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | app_name              | String                | App name.                                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | app_remark            | String                | App description.                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | app_type              | String                | App type.                                                                             |
   |                       |                       |                                                                                       |
   |                       |                       | The default value is apig. Other types are not supported currently.                   |
   |                       |                       |                                                                                       |
   |                       |                       | Enumeration values:                                                                   |
   |                       |                       |                                                                                       |
   |                       |                       | -  **apig**                                                                           |
   |                       |                       |                                                                                       |
   |                       |                       | -  **roma**                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | app_creator           | String                | Creator of the app.                                                                   |
   |                       |                       |                                                                                       |
   |                       |                       | -  USER: The app is created by a tenant.                                              |
   |                       |                       |                                                                                       |
   |                       |                       | -  MARKET: The app is allocated by KooGallery. This value is not supported currently. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | publish_id            | String                | API publication record ID.                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | group_id              | String                | ID of the API group to which the API belongs.                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | auth_tunnel           | String                | Authorization channel type.                                                           |
   |                       |                       |                                                                                       |
   |                       |                       | -  NORMAL: normal channel                                                             |
   |                       |                       |                                                                                       |
   |                       |                       | -  GREEN: green channel                                                               |
   |                       |                       |                                                                                       |
   |                       |                       | The default value is NORMAL. This parameter is not supported currently.               |
   |                       |                       |                                                                                       |
   |                       |                       | Enumeration values:                                                                   |
   |                       |                       |                                                                                       |
   |                       |                       | -  **NORMAL**                                                                         |
   |                       |                       |                                                                                       |
   |                       |                       | -  **GREEN**                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | auth_whitelist        | Array of strings      | Whitelist for the green channel.                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | auth_blacklist        | Array of strings      | Blacklist for the green channel.                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | visit_param           | String                | Access parameters.                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | roma_app_type         | String                | ROMA application type.                                                                |
   |                       |                       |                                                                                       |
   |                       |                       | -  subscription: subscription application                                             |
   |                       |                       |                                                                                       |
   |                       |                       | -  integration: integration application                                               |
   |                       |                       |                                                                                       |
   |                       |                       | Currently, this parameter is not supported.                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | env_name              | String                | Name of the environment in which the app has been authorized to call the API.         |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | app_id                | String                | App ID.                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+

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
     "total" : 1,
     "size" : 1,
     "auths" : [ {
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "app_name" : "app_demo",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
       "group_name" : "api_group_001",
       "api_type" : 1,
       "api_name" : "Api_http",
       "app_id" : "356de8eb7a8742168586e5daf5339965",
       "auth_time" : "2020-08-04T04:02:22Z",
       "app_creator" : "USER",
       "id" : "dd29b33ae4394e3b924b582c6b40880b",
       "api_remark" : "Web backend Api",
       "auth_role" : "PROVIDER",
       "app_type" : "apig",
       "auth_tunnel" : "NORMAL",
       "publish_id" : "40e7162dc6b94bbbbb1a60d2a24b1b0c"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:api_name. Please refer to the support documentation"
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
     "error_code" : "APIG.3004",
     "error_msg" : "App 356de8eb7a8742168586e5daf5339965 does not exist"
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
