:original_name: ListSignatureKeysBindedToApiV2_1.html

.. _ListSignatureKeysBindedToApiV2_1:

Querying Signature Keys Bound to an API
=======================================

Function
--------

This API is used to query the signature keys that have been bound to a specified API. Only one signature key can be bound to an API in an environment.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/sign-bindings/binded-signs

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
   | api_id          | Yes             | String          | API ID.                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_id         | No              | String          | Signature key ID.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_name       | No              | String          | Signature key name.                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_id          | No              | String          | Environment ID.                                                                                                                                                                     |
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

   +-----------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                                       | Description                                          |
   +===========+============================================================================================================+======================================================+
   | size      | Integer                                                                                                    | Length of the returned resource list.                |
   +-----------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                                       | Number of resources that match the query conditions. |
   +-----------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | bindings  | Array of :ref:`SignApiBindingInfo <listsignaturekeysbindedtoapiv2_1__response_signapibindinginfo>` objects | APIs bound to the signature key.                     |
   +-----------+------------------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listsignaturekeysbindedtoapiv2_1__response_signapibindinginfo:

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
   | sign_key              | String                | Signature key.                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  hmac: The value contains 8 to 32 characters, including letters, digits, underscores (_), and hyphens (-). It must start with a letter or digit. If not specified, a key is automatically generated.                                                                                                                           |
   |                       |                       | -  basic: The value contains 4 to 32 characters, including letters, digits, underscores (_), and hyphens (-). It must start with a letter. If not specified, a key is automatically generated.                                                                                                                                   |
   |                       |                       | -  public_key: The value contains 8 to 512 characters, including letters, digits, and special characters ``(_-+/=).`` It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a key is automatically generated.                                                                                       |
   |                       |                       | -  aes: The value contains 16 characters if the aes-128-cfb algorithm is used, or 32 characters if the aes-256-cfb algorithm is used. Letters, digits, and special characters (``_-!@#$%+/=``) are allowed. It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a key is automatically generated. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_secret           | String                | Signature secret.                                                                                                                                                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  hmac: The value contains 16 to 64 characters. Letters, digits, and special characters ``(_-!@#$%)`` are allowed. It must start with a letter or digit. If not specified, a value is automatically generated.                                                                                                                  |
   |                       |                       | -  basic: The value contains 8 to 64 characters. Letters, digits, and special characters ``(_-!@#$%)`` are allowed. It must start with a letter or digit. If not specified, a value is automatically generated.                                                                                                                  |
   |                       |                       | -  public_key: The value contains 15 to 2048 characters, including letters, digits, and special characters (``_-!@#$%+/=``). It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a value is automatically generated.                                                                              |
   |                       |                       | -  aes: The value contains 16 characters, including letters, digits, and special characters (``_-!@#$%+/=``). It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a value is automatically generated.                                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_type             | String                | Signature key type.                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  hmac                                                                                                                                                                                                                                                                                                                          |
   |                       |                       | -  basic                                                                                                                                                                                                                                                                                                                         |
   |                       |                       | -  public_key                                                                                                                                                                                                                                                                                                                    |
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
   |                       |                       | -  **basic**                                                                                                                                                                                                                                                                                                                     |
   |                       |                       | -  **public_key**                                                                                                                                                                                                                                                                                                                |
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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 1,
     "size" : 1,
     "bindings" : [ {
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "group_name" : "api_group_001",
       "binding_time" : "2020-08-03T04:00:11Z",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "sign_id" : "0b0e8f456b8742218af75f945307173c",
       "sign_name" : "signature_demo",
       "sign_key" : "a071a20d460a4f639a636c3d7e3d8163",
       "sign_secret" : "dc0************2b3",
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
     "error_code" : "APIG.3002",
     "error_msg" : "API 5f918d104dc84480a75166ba99efff21 does not exist"
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
