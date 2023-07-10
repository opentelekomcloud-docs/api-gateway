:original_name: ListSignatureKeysV2.html

.. _ListSignatureKeysV2:

Querying Signature Keys
=======================

Function
--------

This API is used to query all the signature keys.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/signs

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

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
   | id              | No              | String          | Signature key ID.                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Signature key name.                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | precise_search  | No              | String          | Parameter name (name) for exact matching.                                                                                                                                           |
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

   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                              | Description                                          |
   +===========+===================================================================================================+======================================================+
   | size      | Integer                                                                                           | Length of the returned resource list.                |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                              | Number of resources that match the query conditions. |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+
   | signs     | Array of :ref:`SignatureWithBindNum <listsignaturekeysv2__response_signaturewithbindnum>` objects | Signature key list.                                  |
   +-----------+---------------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listsignaturekeysv2__response_signaturewithbindnum:

.. table:: **Table 5** SignatureWithBindNum

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
   | bind_num              | Integer               | Number of bound APIs.                                                                                                                                                                                                                                                                                                            |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ldapi_bind_num        | Integer               | Number of custom backends bound.                                                                                                                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                                                                                                                                                  |
   |                       |                       | Currently, this parameter is not supported.                                                                                                                                                                                                                                                                                      |
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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 2,
     "size" : 2,
     "signs" : [ {
       "sign_secret" : "signsecretsignsecretsignsecretsignsecret",
       "update_time" : "2018-02-07T02:00:27.964766Z",
       "create_time" : "2018-02-06T12:17:36Z",
       "name" : "signature_demo",
       "id" : "0b0e8f456b8742218af75f945307173c",
       "sign_key" : "signkeysignkey",
       "sign_type" : "hmac",
       "bind_num" : 0,
       "ldapi_bind_num" : 0
     }, {
       "sign_secret" : "9ce16b029034464898ee33540c42e16a",
       "update_time" : "2020-07-30T03:56:58Z",
       "create_time" : "2020-07-30T03:56:58Z",
       "name" : "Signature_udlu",
       "id" : "9dc388382fba485aadd19f932303f4c9",
       "sign_key" : "ca50c5b670044c83b5b890a9a68a30d5",
       "sign_type" : "hmac",
       "bind_num" : 0,
       "ldapi_bind_num" : 0
     } ]
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
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
