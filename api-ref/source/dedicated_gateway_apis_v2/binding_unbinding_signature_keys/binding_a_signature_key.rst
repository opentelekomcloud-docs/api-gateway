:original_name: AssociateSignatureKeyV2.html

.. _AssociateSignatureKeyV2:

Binding a Signature Key
=======================

Function
--------

A signature key takes effect only after being bound to an API.

When requesting the backend service, APIG uses the signature key to cryptographically sign requests. The backend service verifies the signature to identify request sources.

This API is used to bind a signature key to one or more published APIs. You can bind different signature keys to an API in different environments, but can bind only one signature key to the API in each environment.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/sign-bindings

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

   =========== ========= ================ ==========================
   Parameter   Mandatory Type             Description
   =========== ========= ================ ==========================
   sign_id     Yes       String           Signature key ID.
   publish_ids Yes       Array of strings API publication record ID.
   =========== ========= ================ ==========================

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------------------+----------------------------------+
   | Parameter | Type                                                                                              | Description                      |
   +===========+===================================================================================================+==================================+
   | bindings  | Array of :ref:`SignApiBindingInfo <associatesignaturekeyv2__response_signapibindinginfo>` objects | APIs bound to the signature key. |
   +-----------+---------------------------------------------------------------------------------------------------+----------------------------------+

.. _associatesignaturekeyv2__response_signapibindinginfo:

.. table:: **Table 5** SignApiBindingInfo

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================================================================================+
   | publish_id            | String                | API publication record ID.                                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_id                | String                | API ID.                                                                                                                                                                                                                                                                                                                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_name            | String                | Name of the API group to which the API belongs.                                                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | binding_time          | String                | Binding time.                                                                                                                                                                                                                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id                | String                | ID of the environment in which the API has been published.                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_name              | String                | Name of the environment in which the API has been published.                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_type              | Integer               | API type.                                                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_name              | String                | API name.                                                                                                                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Binding record ID.                                                                                                                                                                                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | api_remark            | String                | API description.                                                                                                                                                                                                                                                                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_id               | String                | Signature key ID.                                                                                                                                                                                                                                                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_name             | String                | Signature key name. It can contain 3 to 64 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | req_method            | String                | Request method.                                                                                                                                                                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **GET**                                                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **POST**                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **DELETE**                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **PUT**                                                                                                                                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **PATCH**                                                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **HEAD**                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **OPTIONS**                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **ANY**                                                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_key              | String                | Signature key.                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  hmac: The value contains 8 to 32 characters, including letters, digits, underscores (_), and hyphens (-). It must start with a letter or digit. If not specified, a key is automatically generated.                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  basic: The value contains 4 to 32 characters, including letters, digits, underscores (_), and hyphens (-). It must start with a letter. If not specified, a key is automatically generated.                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  public_key: The value contains 8 to 512 characters, including letters, digits, and special characters ``(_-+/=).`` It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a key is automatically generated.                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  aes: The value contains 16 characters if the aes-128-cfb algorithm is used, or 32 characters if the aes-256-cfb algorithm is used. Letters, digits, and special characters (``_-!@#$%+/=``) are allowed. It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a key is automatically generated. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_secret           | String                | Signature secret.                                                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  hmac: The value contains 16 to 64 characters. Letters, digits, and special characters ``(_-!@#$%)`` are allowed. It must start with a letter or digit. If not specified, a value is automatically generated.                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  basic: The value contains 8 to 64 characters. Letters, digits, and special characters ``(_-!@#$%)`` are allowed. It must start with a letter or digit. If not specified, a value is automatically generated.                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  public_key: The value contains 15 to 2048 characters, including letters, digits, and special characters (``_-!@#$%+/=``). It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a value is automatically generated.                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  aes: The value contains 16 characters, including letters, digits, and special characters (``_-!@#$%+/=``). It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a value is automatically generated.                                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_type             | String                | Signature key type.                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  hmac                                                                                                                                                                                                                                                                                                                          |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  basic                                                                                                                                                                                                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  public_key                                                                                                                                                                                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  aes                                                                                                                                                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | To use a basic signature key, ensure that your gateway version supports it. If your gateway does not support this type of signature key, contact technical support to upgrade your gateway.                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | To use a public_key signature key, ensure that the public_key feature has been configured for your gateway. For details, see "Appendix" > "Supported Features". If your gateway does not support this feature, contact technical support to enable it.                                                                           |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | To use an AES signature key, ensure that your gateway version supports it. If your gateway does not support this type of signature key, contact technical support to upgrade your gateway.                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **hmac**                                                                                                                                                                                                                                                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **basic**                                                                                                                                                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **public_key**                                                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **aes**                                                                                                                                                                                                                                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Binding a signature key to a published API

.. code-block::

   {
     "sign_id" : "0b0e8f456b8742218af75f945307173c",
     "publish_ids" : [ "40e7162dc6b94bbbbb1a60d2a24b1b0c" ]
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "bindings" : [ {
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "sign_secret" : "dc0************2b3",
       "group_name" : "api_group_001",
       "sign_id" : "0b0e8f456b8742218af75f945307173c",
       "sign_key" : "a071a20d460a4f639a636c3d7e3d8163",
       "binding_time" : "2020-08-03T04:00:11.638167852Z",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "sign_name" : "signature_demo",
       "api_type" : 1,
       "api_name" : "Api_http",
       "id" : "25082bd52f74442bb1d273993d567938",
       "api_remark" : "Web backend API"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:sign_id. Please refer to the support documentation"
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
