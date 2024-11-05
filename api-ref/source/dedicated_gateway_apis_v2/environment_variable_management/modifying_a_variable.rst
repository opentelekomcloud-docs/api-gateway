:original_name: UpdateEnvironmentVariableV2.html

.. _UpdateEnvironmentVariableV2:

Modifying a Variable
====================

Function
--------

This API is used to modify an environment variable. If an environment variable is referenced by the backend service address of an API, modifying the environment variable will publish all APIs that use the variable again.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/env-variables/{env_variable_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                             |
   +=================+===========+========+=========================================================================================================+
   | project_id      | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id     | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | env_variable_id | Yes       | String | Environment variable ID.                                                                                |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                           |
   +================+===========+========+=======================================================================================================================+
   | variable_value | Yes       | String | The variable value can contain 1 to 255 characters. Only letters, digits, and special characters (_-/.:) are allowed. |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                |
   +=======================+=======================+============================================================================================================================================================================================================================================================================================================================================================+
   | variable_value        | String                | The variable value can contain 1 to 255 characters. Only letters, digits, and special characters (_-/.:) are allowed.                                                                                                                                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id                | String                | Environment ID.                                                                                                                                                                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                            |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                            |
   |                       |                       | Maximum: **65**                                                                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id              | String                | API group ID.                                                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                            |
   |                       |                       | Minimum: **1**                                                                                                                                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                                            |
   |                       |                       | Maximum: **65**                                                                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | variable_name         | String                | Variable name, which can contain 3 to 32 characters, starting with a letter. Only letters, digits, hyphens (-), and underscores (_) are allowed. The variable name is equivalent to "#Name#" in API definitions. Characters between the number signs are case-sensitive. The variable name will be replaced with the variable value after API publication. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Environment variable ID.                                                                                                                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==================
   Parameter  Type   Description
   ========== ====== ==================
   error_code String Error code.
   error_msg  String Error description.
   ========== ====== ==================

Example Requests
----------------

.. code-block::

   {
     "variable_value" : "192.168.1.5"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "variable_value" : "192.168.1.5",
     "env_id" : "7a1ad0c350844ee69479b47df9a881cb",
     "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
     "id" : "25054838a624400bbf2267cf5b3a3f70",
     "variable_name" : "address"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:variable_name"
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
     "error_code" : "APIG.3003",
     "error_msg" : "Environment 7a1ad0c350844ee69479b47df9a881cb does not exist"
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
