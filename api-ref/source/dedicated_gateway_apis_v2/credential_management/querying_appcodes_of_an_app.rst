:original_name: ListAppCodesV2_1.html

.. _ListAppCodesV2_1:

Querying AppCodes of an App
===========================

Function
--------

This API is used to query the AppCodes of an app.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/apps/{app_id}/app-codes

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

   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                 | Description                                          |
   +===========+======================================================================================+======================================================+
   | size      | Integer                                                                              | Length of the returned resource list.                |
   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                 | Number of resources that match the query conditions. |
   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+
   | app_codes | Array of :ref:`AppCodeBaseInfo <listappcodesv2_1__response_appcodebaseinfo>` objects | AppCode list.                                        |
   +-----------+--------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listappcodesv2_1__response_appcodebaseinfo:

.. table:: **Table 5** AppCodeBaseInfo

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================================================================+
   | app_code              | String                | AppCode value.                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                         |
   |                       |                       | It can contain 64 to 180 characters, starting with a letter, digit, plus sign (+), or slash (/). Only letters, digits, and the following special characters are allowed: ``+_!@#$%-/=`` |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | ID.                                                                                                                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | app_id                | String                | App ID.                                                                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                                                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
     "app_codes" : [ {
       "app_code" : "GjOD3g80AABuuFeEJpVQADBlAjBh3UzC7W+gr4VJBB5BtJ4fdVOQoSvoji3gFxUDb5pWBz9wUcw9+8/bFZ1B/4pq29wCMQC0pQWX6zTndljDEl99As1pw+WntAU9xcq+ffagoH6zDpKUvdxV6Ezj8LcCcPZN6BU=",
       "app_id" : "9ed8b7fe84224de681e7d7a5587e76dc",
       "id" : "32dc8ca22d1b4b9cb94022186880576b",
       "create_time" : "2020-07-24T02:37:24Z"
     }, {
       "app_code" : "fdc8d90a30174460a91ddacfa54d6f04c92e523a85cc4a1894f87cb13b6f572a",
       "app_id" : "9ed8b7fe84224de681e7d7a5587e76dc",
       "id" : "b3d34f746d0847fb95138670e10207ed",
       "create_time" : "2020-07-24T02:31:45Z"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:app_id. Please refer to the support documentation"
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
     "error_msg" : "App 9ed8b7fe84224de681e7d7a5587e76dc does not exist"
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
