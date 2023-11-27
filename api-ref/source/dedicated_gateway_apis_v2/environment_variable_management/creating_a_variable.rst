:original_name: CreateEnvironmentVariableV2_1.html

.. _CreateEnvironmentVariableV2_1:

Creating a Variable
===================

Function
--------

Publishing an API in different environments may involve various variables, such as API service deployment address and request version.

You can define environment variables when creating an API. When the API is called, the environment variables will be replaced with the variable values to distinguish environments.

Environment variables are defined for an API group and apply to all APIs in the group.

.. note::

   #. Environment variable names must be unique for an API group in the same environment.

   #. Environment variable names are case-sensitive. For example, ABC and abc are two different variables.

   #. APIs that use environment variables cannot be debugged.

   #. You must enclose an environment variable in number signs (#) so that it can be replaced with the actual value of the environment in which the API is published. For example, if the URL of an API is https://#address#:8080 and the value of variable address is 192.168.1.5 in the RELEASE environment, the real URL of the API is https://192.168.1.5:8080 after publishing.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/env-variables

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

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================================================================================================================================================================================+
   | variable_value  | Yes             | String          | The variable value can contain 1 to 255 characters. Only letters, digits, and special characters (_-/.:) are allowed.                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | Yes             | String          | Environment ID.                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 | Maximum: **65**                                                                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | Yes             | String          | API group ID.                                                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                            |
   |                 |                 |                 | Maximum: **65**                                                                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | variable_name   | Yes             | String          | Variable name, which can contain 3 to 32 characters, starting with a letter. Only letters, digits, hyphens (-), and underscores (_) are allowed. The variable name is equivalent to "#Name#" in API definitions. Characters between the number signs are case-sensitive. The variable name will be replaced with the variable value after API publication. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

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

Creating an environment variable

.. code-block::

   {
     "variable_name" : "address",
     "variable_value" : "192.168.1.5",
     "env_id" : "7a1ad0c350844ee69479b47df9a881cb",
     "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600"
   }

Example Responses
-----------------

**Status code: 201**

Created

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
     "error_msg" : "Invalid parameter value,parameterName:instance_id. Please refer to the support documentation"
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
     "error_msg" : "The instance does not exist;id:f0fa1789-3b76-433b-a787-9892951c620ec"
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
