:original_name: ListAppsV2.html

.. _ListAppsV2:

Querying Apps
=============

Function
--------

This API is used to query apps.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/apps

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
   | id              | No              | String          | App ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | App name.                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | Integer         | App status.                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_key         | No              | String          | AppKey.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | creator         | No              | String          | Creator of the app.                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  USER: The app is created by an API user.                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  MARKET: This parameter is not used currently.                                                                                                                                    |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | precise_search  | No              | String          | Parameter name (name) for exact matching.                                                                                                                                           |
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

   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                 | Description                                          |
   +===========+======================================================================================+======================================================+
   | size      | Integer                                                                              | Length of the returned resource list.                |
   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                 | Number of resources that match the query conditions. |
   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | apps      | Array of :ref:`AppInfoWithBindNum <listappsv2__response_appinfowithbindnum>` objects | App list.                                            |
   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listappsv2__response_appinfowithbindnum:

.. table:: **Table 5** AppInfoWithBindNum

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
   | bind_num              | Integer               | Number of bound APIs.                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------+

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 2,
     "size" : 2,
     "apps" : [ {
       "bind_num" : 0,
       "creator" : "USER",
       "update_time" : "2020-08-03T13:09:13Z",
       "app_key" : "ee8f878c252747028f07eb116c2cd91b",
       "name" : "app_demo",
       "remark" : "Demo app",
       "id" : "356de8eb7a8742168586e5daf5339965",
       "app_secret" : "416b6b2a1d394111b9bc1df0e6842ab8",
       "register_time" : "2020-08-03T13:09:13Z",
       "status" : 1,
       "app_type" : "apig"
     }, {
       "bind_num" : 3,
       "creator" : "USER",
       "update_time" : "2020-05-27T10:38:03.133586Z",
       "app_key" : "840b8b5b1efc4ec686639759c2c584da",
       "name" : "app_001",
       "id" : "9ed8b7fe84224de681e7d7a5587e76dc",
       "app_secret" : "0a4e7035e81e424ab4c2c571980d5c6e",
       "register_time" : "2020-03-28T11:09:06Z",
       "status" : 1
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
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
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
