:original_name: ListApisNotBoundWithSignatureKeyV2.html

.. _ListApisNotBoundWithSignatureKeyV2:

Querying APIs Not Bound with a Signature Key
============================================

Function
--------

This API is used to query the APIs to which a signature key has not been bound. Only published APIs will be displayed.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/sign-bindings/unbinded-apis

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
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
   | sign_id         | Yes             | String          | Signature key ID.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | No              | String          | Environment ID.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_id          | No              | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_name        | No              | String          | API name.                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id        | No              | String          | API group ID.                                                                                                                                                                       |
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

   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                         | Description                                          |
   +===========+==============================================================================================+======================================================+
   | size      | Integer                                                                                      | Length of the returned resource list.                |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                         | Number of resources that match the query conditions. |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+
   | apis      | Array of :ref:`ApiForSign <listapisnotboundwithsignaturekeyv2__response_apiforsign>` objects | API list.                                            |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listapisnotboundwithsignaturekeyv2__response_apiforsign:

.. table:: **Table 5** ApiForSign

   +-----------------------+-----------------------+--------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                  |
   +=======================+=======================+==============================================================+
   | auth_type             | String                | API authentication mode.                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | run_env_name          | String                | Name of the environment in which the API has been published. |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | group_name            | String                | Name of the API group to which the API belongs.              |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | publish_id            | String                | Publication record ID.                                       |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | group_id              | String                | ID of the API group to which the API belongs.                |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | name                  | String                | API name.                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | remark                | String                | API description.                                             |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | run_env_id            | String                | ID of the environment in which the API has been published.   |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | id                    | String                | API ID.                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | req_uri               | String                | API request address.                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | type                  | Integer               | API type.                                                    |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | signature_name        | String                | Name of the signature key bound to the API.                  |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | req_method            | String                | Request method.                                              |
   |                       |                       |                                                              |
   |                       |                       | Enumeration values:                                          |
   |                       |                       |                                                              |
   |                       |                       | -  **GET**                                                   |
   |                       |                       |                                                              |
   |                       |                       | -  **POST**                                                  |
   |                       |                       |                                                              |
   |                       |                       | -  **DELETE**                                                |
   |                       |                       |                                                              |
   |                       |                       | -  **PUT**                                                   |
   |                       |                       |                                                              |
   |                       |                       | -  **PATCH**                                                 |
   |                       |                       |                                                              |
   |                       |                       | -  **HEAD**                                                  |
   |                       |                       |                                                              |
   |                       |                       | -  **OPTIONS**                                               |
   |                       |                       |                                                              |
   |                       |                       | -  **ANY**                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------+

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
     "total" : 1,
     "size" : 1,
     "apis" : [ {
       "run_env_name" : "RELEASE",
       "group_name" : "api_group_001",
       "remark" : "Mock backend API",
       "publish_id" : "9f27d1dc4f4242a9abf88e563dbfc33d",
       "group_id" : "c77f5e81d9cb4424bf704ef2b0ac7600",
       "name" : "Api_mock",
       "run_env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "id" : "3a955b791bd24b1c9cd94c745f8d1aad",
       "type" : 1,
       "auth_type" : "IAM",
       "req_uri" : "/test/mock"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:api_name. Please refer to the support documentation"
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
     "error_code" : "APIG.3017",
     "error_msg" : "Signature key 0b0e8f456b8742218af75f945307173c does not exist"
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
