:original_name: CreateAuthorizingAppsV2_1.html

.. _CreateAuthorizingAppsV2_1:

Authorizing Apps
================

Function
--------

An app cannot access any APIs after being created. To access an API in a specific environment, bind the app to the API in the environment.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/app-auths

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------+-----------+------------------+-------------------------------------------------------------+
   | Parameter | Mandatory | Type             | Description                                                 |
   +===========+===========+==================+=============================================================+
   | env_id    | Yes       | String           | ID of the environment in which the apps will be authorized. |
   +-----------+-----------+------------------+-------------------------------------------------------------+
   | app_ids   | Yes       | Array of strings | App IDs.                                                    |
   +-----------+-----------+------------------+-------------------------------------------------------------+
   | api_ids   | Yes       | Array of strings | API list.                                                   |
   +-----------+-----------+------------------+-------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------+-------------------------------------------------------------------------------------------------+----------------------------+
   | Parameter | Type                                                                                            | Description                |
   +===========+=================================================================================================+============================+
   | auths     | Array of :ref:`ApiAuthRelations <createauthorizingappsv2_1__response_apiauthrelations>` objects | App authorization records. |
   +-----------+-------------------------------------------------------------------------------------------------+----------------------------+

.. _createauthorizingappsv2_1__response_apiauthrelations:

.. table:: **Table 5** ApiAuthRelations

   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                                                                      | Description                                                             |
   +=======================+===========================================================================+=========================================================================+
   | api_id                | String                                                                    | API ID.                                                                 |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | auth_result           | :ref:`AuthResult <createauthorizingappsv2_1__response_authresult>` object | Authorization result.                                                   |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | auth_time             | String                                                                    | Authorization time.                                                     |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | id                    | String                                                                    | Authorization record ID.                                                |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | app_id                | String                                                                    | App ID.                                                                 |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | auth_role             | String                                                                    | Authorizer.                                                             |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  PROVIDER: API provider                                               |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  CONSUMER: API user                                                   |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | Enumeration values:                                                     |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  **PROVIDER**                                                         |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  **CONSUMER**                                                         |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | auth_tunnel           | String                                                                    | Authorization channel type.                                             |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  NORMAL: normal channel                                               |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  GREEN: green channel                                                 |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | The default value is NORMAL. This parameter is not supported currently. |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | Enumeration values:                                                     |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  **NORMAL**                                                           |
   |                       |                                                                           |                                                                         |
   |                       |                                                                           | -  **GREEN**                                                            |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | auth_whitelist        | Array of strings                                                          | Whitelist for the green channel.                                        |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | auth_blacklist        | Array of strings                                                          | Blacklist for the green channel.                                        |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+
   | visit_params          | String                                                                    | Access parameters.                                                      |
   +-----------------------+---------------------------------------------------------------------------+-------------------------------------------------------------------------+

.. _createauthorizingappsv2_1__response_authresult:

.. table:: **Table 6** AuthResult

   +-----------------------+-----------------------+------------------------------------------------+
   | Parameter             | Type                  | Description                                    |
   +=======================+=======================+================================================+
   | status                | String                | Authorization result.                          |
   |                       |                       |                                                |
   |                       |                       | -  SUCCESS                                     |
   |                       |                       |                                                |
   |                       |                       | -  SKIPPED                                     |
   |                       |                       |                                                |
   |                       |                       | -  FAILED                                      |
   |                       |                       |                                                |
   |                       |                       | Enumeration values:                            |
   |                       |                       |                                                |
   |                       |                       | -  **SUCCESS**                                 |
   |                       |                       |                                                |
   |                       |                       | -  **SKIPPED**                                 |
   |                       |                       |                                                |
   |                       |                       | -  **FAILED**                                  |
   +-----------------------+-----------------------+------------------------------------------------+
   | error_msg             | String                | Error message.                                 |
   +-----------------------+-----------------------+------------------------------------------------+
   | error_code            | String                | Error code.                                    |
   +-----------------------+-----------------------+------------------------------------------------+
   | api_name              | String                | Name of the API for which authorization fails. |
   +-----------------------+-----------------------+------------------------------------------------+
   | app_name              | String                | Name of the app that fails to be authorized.   |
   +-----------------------+-----------------------+------------------------------------------------+

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

Authorizing an app to call an API

.. code-block::

   {
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
     "app_ids" : [ "356de8eb7a8742168586e5daf5339965" ],
     "api_ids" : [ "5f918d104dc84480a75166ba99efff21" ]
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "auths" : [ {
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "auth_result" : {
         "status" : "SUCCESS"
       },
       "auth_time" : "22020-08-04T04:02:22.482227344Z",
       "id" : "dd29b33ae4394e3b924b582c6b40880b",
       "app_id" : "356de8eb7a8742168586e5daf5339965",
       "auth_role" : "PROVIDER",
       "auth_tunnel" : "NORMAL"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
     "error_msg" : "Invalid parameter value,parameterName:api_ids. Please refer to the support documentation"
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
