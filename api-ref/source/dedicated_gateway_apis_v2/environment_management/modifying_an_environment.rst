:original_name: UpdateEnvironmentV2.html

.. _UpdateEnvironmentV2:

Modifying an Environment
========================

Function
--------

This API is used to modify the information about an environment. Only the name and remark attributes of an environment can be modified.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/envs/{env_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | env_id      | Yes       | String | Environment ID.                                                                                                       |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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

**Status code: 200**

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

.. code-block::

   {
     "name" : "DEV",
     "remark" : "Development environment"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "create_time" : "2020-07-31T06:41:43Z",
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
