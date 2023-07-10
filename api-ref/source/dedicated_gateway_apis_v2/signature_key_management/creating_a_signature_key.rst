:original_name: CreateSignatureKeyV2.html

.. _CreateSignatureKeyV2:

Creating a Signature Key
========================

Function
--------

It is a good practice to provide a protection mechanism for APIs to ensure access security. For example, authenticating API request sources and denying the access from unauthorized sources.A signature key is a protection mechanism in case.Create a signature key and bind it to an API. When requesting the API, APIG uses the signature key to encrypt request parameter data and generate a signature. The backend service of the API verifies requests by using the signature. Unauthorized requests will be denied to protect the API against attacks from unknown sources.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/signs

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
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

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================================+
   | name            | Yes             | String          | Signature key name. It can contain letters, digits, and underscores(_) and must start with a letter.                                                                                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Minimum: **3**                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Maximum: **64**                                                                                                                                                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_type       | No              | String          | Signature key type.                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  hmac                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  basic                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  public_key                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  aes                                                                                                                                                                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | To use a basic signature key, ensure that your gateway version supports it. If your gateway does not support this type of signature key, contact technical support to upgrade your gateway.                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | To use a public_key signature key, ensure that the public_key feature has been configured for your gateway. For details, see "Appendix" > "Supported Features". If your gateway does not support this feature, contact technical support to enable it.                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | To use an AES signature key, ensure that your gateway version supports it. If your gateway does not support this type of signature key, contact technical support to upgrade your gateway.                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  **hmac**                                                                                                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  **basic**                                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  **public_key**                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  **aes**                                                                                                                                                                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_key        | No              | String          | Signature key.                                                                                                                                                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  hmac: The value contains 8 to 32 characters, including letters, digits, underscores (_), and hyphens (-). It must start with a letter or digit. If not specified, a key is automatically generated.                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  basic: The value contains 4 to 32 characters, including letters, digits, underscores (_), and hyphens (-). It must start with a letter. If not specified, a key is automatically generated.                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  public_key: The value contains 8 to 512 characters, including letters, digits, and special characters ``(_-+/=).`` It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a key is automatically generated.                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  aes: The value contains 16 characters if the aes-128-cfb algorithm is used, or 32 characters if the aes-256-cfb algorithm is used. Letters, digits, and special characters (``_-!@#$%+/=``) are allowed. It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a key is automatically generated. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_secret     | No              | String          | Signature secret.                                                                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  hmac: The value contains 16 to 64 characters. Letters, digits, and special characters ``(_-!@#$%)`` are allowed. It must start with a letter or digit. If not specified, a value is automatically generated.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  basic: The value contains 8 to 64 characters. Letters, digits, and special characters ``(_-!@#$%)`` are allowed. It must start with a letter or digit. If not specified, a value is automatically generated.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  public_key: The value contains 15 to 2048 characters, including letters, digits, and special characters (``_-!@#$%+/=``). It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a value is automatically generated.                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  aes: The value contains 16 characters, including letters, digits, and special characters (``_-!@#$%+/=``). It must start with a letter, digit, plus sign (+), or slash (/). If not specified, a value is automatically generated.                                                                                             |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sign_algorithm  | No              | String          | Signature algorithm. Specify a signature algorithm only when using an AES signature key. By default, no algorithm is used.                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  **aes-128-cfb**                                                                                                                                                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  **aes-256-cfb**                                                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================================================================================================================================+
   | name                  | String                | Signature key name. It can contain letters, digits, and underscores(_) and must start with a letter.                                                                                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Minimum: **3**                                                                                                                                                                                                                                                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Maximum: **64**                                                                                                                                                                                                                                                                                                                  |
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
   | sign_algorithm        | String                | Signature algorithm. Specify a signature algorithm only when using an AES signature key. By default, no algorithm is used.                                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Enumeration values:                                                                                                                                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **aes-128-cfb**                                                                                                                                                                                                                                                                                                               |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | -  **aes-256-cfb**                                                                                                                                                                                                                                                                                                               |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time.                                                                                                                                                                                                                                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                                                                                                                                                                                                                                                                                   |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Signature key ID.                                                                                                                                                                                                                                                                                                                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. code-block::

   {
     "name" : "signature_demo",
     "sign_key" : "signkeysignkey",
     "sign_secret" : "signsecretsignsecretsignsecretsignsecret"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "sign_secret" : "signsecretsignsecretsignsecretsignsecret",
     "update_time" : "2020-08-03T03:39:38.119032888Z",
     "create_time" : "2020-08-03T03:39:38.119032659Z",
     "name" : "signature_demo",
     "id" : "0b0e8f456b8742218af75f945307173c",
     "sign_key" : "signkeysignkey",
     "sign_type" : "hmac"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
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
