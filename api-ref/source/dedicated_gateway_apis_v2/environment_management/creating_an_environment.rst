:original_name: CreateEnvironmentV2_1.html

.. _CreateEnvironmentV2_1:

Creating an Environment
=======================

Function
--------

API providers can publish an API in different environments, such as the development, test, and production environments.

API information, such as the version, request address, and even request message, varies depending on the environment in which an API is published. For example, v1.0 of an API is published in the production environment, v1.1 in the test environment, and v1.2 in the development environment.

APIG provides environment management, enabling you to access APIG in different scenarios at minimal costs.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/envs

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

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                            |
   +=================+=================+=================+========================================================================================================+
   | name            | Yes             | String          | Environment name, which can contain letters, digits, and underscores (_) and must start with a letter. |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Minimum: **3**                                                                                         |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Maximum: **64**                                                                                        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+
   | remark          | No              | String          | Description.                                                                                           |
   |                 |                 |                 |                                                                                                        |
   |                 |                 |                 | Maximum: **255**                                                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   =========== ====== =================
   Parameter   Type   Description
   =========== ====== =================
   create_time String Creation time.
   name        String Environment name.
   remark      String Description.
   id          String Environment ID.
   =========== ====== =================

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

Creating an environment

.. code-block::

   {
     "name" : "DEV",
     "remark" : "Development environment"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "create_time" : "2020-07-31T06:41:43.511347628Z",
     "name" : "DEV",
     "remark" : "Development environment",
     "id" : "7a1ad0c350844ee69479b47df9a881cb"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
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
201         Created
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
