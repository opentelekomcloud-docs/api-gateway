:original_name: CreateFeatureV2.html

.. _CreateFeatureV2:

Configuring a Feature for a Gateway
===================================

Function
--------

This API is used to configure a feature for a gateway.

For details about the supported features and configuration examples, see "Appendix" > "Supported Features" in this document.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/features

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

   +-----------------+-----------------+-----------------+------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                              |
   +=================+=================+=================+==========================================+
   | name            | Yes             | String          | Feature name.                            |
   |                 |                 |                 |                                          |
   |                 |                 |                 | Minimum: **1**                           |
   |                 |                 |                 |                                          |
   |                 |                 |                 | Maximum: **64**                          |
   +-----------------+-----------------+-----------------+------------------------------------------+
   | enable          | Yes             | Boolean         | Indicates whether to enable the feature. |
   +-----------------+-----------------+-----------------+------------------------------------------+
   | config          | No              | String          | Parameter configuration.                 |
   +-----------------+-----------------+-----------------+------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+------------------------------------------+
   | Parameter             | Type                  | Description                              |
   +=======================+=======================+==========================================+
   | id                    | String                | Feature ID.                              |
   +-----------------------+-----------------------+------------------------------------------+
   | name                  | String                | Feature name.                            |
   |                       |                       |                                          |
   |                       |                       | Minimum: **1**                           |
   |                       |                       |                                          |
   |                       |                       | Maximum: **64**                          |
   +-----------------------+-----------------------+------------------------------------------+
   | enable                | Boolean               | Indicates whether to enable the feature. |
   +-----------------------+-----------------------+------------------------------------------+
   | config                | String                | Parameter configuration.                 |
   +-----------------------+-----------------------+------------------------------------------+
   | instance_id           | String                | Gateway ID.                              |
   +-----------------------+-----------------------+------------------------------------------+
   | update_time           | String                | Feature update time.                     |
   +-----------------------+-----------------------+------------------------------------------+

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

Enabling the app_api_key switch

.. code-block::

   {
     "name" : "app_api_key",
     "config" : "on",
     "enable" : true
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "config" : "on",
     "enable" : true,
     "id" : "db9a9260cd3e4a16a9b5747a65d3ffaa",
     "instance_id" : "eddc4d25480b4cd6b512f270a1b8b341",
     "name" : "app_api_key",
     "update_time" : "2020-08-24T01:17:31.041984021Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2000",
     "error_msg" : "unrecognized feature app-api-key"
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
