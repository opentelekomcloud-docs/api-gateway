:original_name: CreateAppCodeV2.html

.. _CreateAppCodeV2:

Creating an AppCode
===================

Function
--------

This API is used to create an AppCode for an app for simple authentication.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/apps/{app_id}/app-codes

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

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================+
   | app_code        | Yes             | String          | AppCode value.                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                         |
   |                 |                 |                 | It can contain 64 to 180 characters, starting with a letter, digit, plus sign (+), or slash (/). Only letters, digits, and the following special characters are allowed: ``+_!@#$%-/=`` |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

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

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

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

Creating an AppCode for simple authentication

.. code-block::

   {
     "app_code" : "GjOD3g80AABuuFeEJpVQADBlAjBh3UzC7W+gr4VJBB5BtJ4fdVOQoSvoji3gFxUDb5pWBz9wUcw9+8/bFZ1B/4pq29wCMQC0pQWX6zTndljDEl99As1pw+WntAU9xcq+ffagoH6zDpKUvdxV6Ezj8LcCcPZN6BU="
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "app_code" : "GjOD3g80AABuuFeEJpVQADBlAjBh3UzC7W+gr4VJBB5BtJ4fdVOQoSvoji3gFxUDb5pWBz9wUcw9+8/bFZ1B/4pq29wCMQC0pQWX6zTndljDEl99As1pw+WntAU9xcq+ffagoH6zDpKUvdxV6Ezj8LcCcPZN6BU=",
     "app_id" : "9ed8b7fe84224de681e7d7a5587e76dc",
     "id" : "32dc8ca22d1b4b9cb94022186880576b",
     "create_time" : "2020-07-24T02:37:24.835128293Z"
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
