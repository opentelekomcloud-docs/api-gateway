:original_name: ShowDetailsOfEnvironmentVariableV2.html

.. _ShowDetailsOfEnvironmentVariableV2:

Querying Variable Details
=========================

Function
--------

This API is used to query the details of an environment variable.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/env-variables/{env_variable_id}

.. table:: **Table 1** Path Parameters

   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                                           |
   +=================+===========+========+=======================================================================================================================+
   | project_id      | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id     | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | env_variable_id | Yes       | String | Environment variable ID.                                                                                              |
   +-----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

**Status code: 401**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 7** Response body parameters

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
     "variable_value" : "192.168.1.5",
     "env_id" : "7a1ad0c350844ee69479b47df9a881cb",
     "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
     "id" : "25054838a624400bbf2267cf5b3a3f70",
     "variable_name" : "address"
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
     "error_code" : "APIG.3011",
     "error_msg" : "The environment variable does not exist, id: 25054838a624400bbf2267cf5b3a3f70"
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
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
