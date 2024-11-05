:original_name: ShowDetailsOfAppV2.html

.. _ShowDetailsOfAppV2:

Querying App Details
====================

Function
--------

This API is used to query the details of an app.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/apps/{app_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | app_id      | Yes       | String | App ID.                                                                                                 |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                         |
   +=======================+=======================+=====================================================================+
   | id                    | String                | ID.                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | name                  | String                | Name.                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | remark                | String                | Description.                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | creator               | String                | Creator of the app.                                                 |
   |                       |                       |                                                                     |
   |                       |                       | -  USER: The app is created by an API user.                         |
   |                       |                       |                                                                     |
   |                       |                       | -  MARKET: The app is allocated by KooGallery.                      |
   |                       |                       |                                                                     |
   |                       |                       | The value MARKET is currently not supported.                        |
   |                       |                       |                                                                     |
   |                       |                       | Enumeration values:                                                 |
   |                       |                       |                                                                     |
   |                       |                       | -  **USER**                                                         |
   |                       |                       |                                                                     |
   |                       |                       | -  **MARKET**                                                       |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | update_time           | String                | Update time.                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | app_key               | String                | AppKey.                                                             |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | app_secret            | String                | AppSecret.                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | register_time         | String                | Registration time.                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | status                | Integer               | Status.                                                             |
   |                       |                       |                                                                     |
   |                       |                       | -  1: valid                                                         |
   |                       |                       |                                                                     |
   |                       |                       | Enumeration values:                                                 |
   |                       |                       |                                                                     |
   |                       |                       | -  **1**                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | app_type              | String                | App type.                                                           |
   |                       |                       |                                                                     |
   |                       |                       | -  apig: APIG app, which is not recommended.                        |
   |                       |                       |                                                                     |
   |                       |                       | -  roma: ROMA integration application.                              |
   |                       |                       |                                                                     |
   |                       |                       | The default value is apig. Other types are not supported currently. |
   |                       |                       |                                                                     |
   |                       |                       | Enumeration values:                                                 |
   |                       |                       |                                                                     |
   |                       |                       | -  **apig**                                                         |
   |                       |                       |                                                                     |
   |                       |                       | -  **roma**                                                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------+
   | roma_app_type         | String                | ROMA application type.                                              |
   |                       |                       |                                                                     |
   |                       |                       | -  subscription: subscription application                           |
   |                       |                       |                                                                     |
   |                       |                       | -  integration: integration application                             |
   |                       |                       |                                                                     |
   |                       |                       | Currently, this parameter is not supported.                         |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

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
     "creator" : "USER",
     "update_time" : "2020-08-03T13:09:13Z",
     "app_key" : "ee8f878c252747028f07eb116c2cd91b",
     "name" : "app_demo",
     "remark" : "Demo app",
     "id" : "356de8eb7a8742168586e5daf5339965",
     "app_secret" : "416************ab8",
     "register_time" : "2020-08-03T13:09:13Z",
     "status" : 1,
     "app_type" : "apig"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:id. Please refer to the support documentation"
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
