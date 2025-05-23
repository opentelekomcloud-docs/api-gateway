:original_name: UpdateCertificateV2.html

.. _UpdateCertificateV2:

Modifying an SSL Certificate
============================

Function
--------

This API is used to modify an SSL certificate.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

PUT /v2/{project_id}/apigw/certificates/{certificate_id}

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                             |
   +================+===========+========+=========================================================================================================+
   | project_id     | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | certificate_id | Yes       | String | Certificate ID.                                                                                         |
   +----------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================+
   | name            | Yes             | String          | Certificate name. It can contain 4 to 50 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | cert_content    | Yes             | String          | Certificate content.                                                                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | private_key     | Yes             | String          | Certificate private key.                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Certificate scope.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Default: **global**                                                                                                                 |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | Enumeration values:                                                                                                                 |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | -  **instance**                                                                                                                     |
   |                 |                 |                 |                                                                                                                                     |
   |                 |                 |                 | -  **global**                                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id     | No              | String          | Gateway ID. This parameter is required if type is set to instance.                                                                  |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | trusted_root_ca | No              | String          | Trusted root certificate (CA).                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                           |
   +========================+=======================+=======================================================================================================================+
   | id                     | String                | Certificate ID.                                                                                                       |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Certificate name.                                                                                                     |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | type                   | String                | Certificate type.                                                                                                     |
   |                        |                       |                                                                                                                       |
   |                        |                       | -  global: Global certificate.                                                                                        |
   |                        |                       |                                                                                                                       |
   |                        |                       | -  instance: Gateway certificate.                                                                                     |
   |                        |                       |                                                                                                                       |
   |                        |                       | Enumeration values:                                                                                                   |
   |                        |                       |                                                                                                                       |
   |                        |                       | -  **global**                                                                                                         |
   |                        |                       |                                                                                                                       |
   |                        |                       | -  **instance**                                                                                                       |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id            | String                | Gateway ID.                                                                                                           |
   |                        |                       |                                                                                                                       |
   |                        |                       | -  If type is set to global, the default value is common.                                                             |
   |                        |                       |                                                                                                                       |
   |                        |                       | -  If type is set to instance, a gateway ID is displayed.                                                             |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | project_id             | String                | Project ID.                                                                                                           |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | common_name            | String                | Domain name.                                                                                                          |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | san                    | Array of strings      | SAN domain name.                                                                                                      |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | not_after              | String                | Expiration time.                                                                                                      |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | signature_algorithm    | String                | Signature algorithm.                                                                                                  |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | create_time            | String                | Creation time.                                                                                                        |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | update_time            | String                | Update time.                                                                                                          |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | is_has_trusted_root_ca | Boolean               | Whether a trusted root certificate (CA) exists. The value is true if trusted_root_ca exists in the bound certificate. |
   |                        |                       |                                                                                                                       |
   |                        |                       | Default: **false**                                                                                                    |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | version                | Integer               | Version.                                                                                                              |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | organization           | Array of strings      | Company or organization.                                                                                              |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | organizational_unit    | Array of strings      | Department.                                                                                                           |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | locality               | Array of strings      | City.                                                                                                                 |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | state                  | Array of strings      | State or province.                                                                                                    |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | country                | Array of strings      | Country or region.                                                                                                    |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | not_before             | String                | Effective time.                                                                                                       |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | serial_number          | String                | Serial number.                                                                                                        |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+
   | issuer                 | Array of strings      | Issuer.                                                                                                               |
   +------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------+

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

Modifying an SSL certificate

.. code-block::

   {
     "name" : "cert_demo",
     "private_key" : "'-----BEGIN PRIVATE KEY-----THIS IS YOUR PRIVATE KEY-----END PRIVATE KEY-----\\n'",
     "cert_content" : "'-----BEGIN CERTIFICATE-----THIS IS YOUR CERT CONTENT-----END CERTIFICATE-----\\n'"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "id" : "a27be832f2e9441c8127fe48e3b5ac67",
     "name" : "cert_demo",
     "common_name" : "apigtest.example.com",
     "san" : [ "apigtest.example.com", "*.san.com" ],
     "version" : 3,
     "organization" : [ "XX" ],
     "organizational_unit" : [ "IT" ],
     "locality" : [ "XX" ],
     "state" : [ "XX" ],
     "country" : [ "XX" ],
     "not_before" : "2019-06-01T00:00:00Z",
     "not_after" : "2031-08-16T06:36:13Z",
     "serial_number" : "13010",
     "issuer" : [ "XXSSL Inc" ],
     "signature_algorithm" : "SHA256-RSA",
     "create_time" : "2021-08-20T02:03:53Z",
     "update_time" : "2021-08-20T02:03:53Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3325",
     "error_msg" : "The dictionary name already exists"
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
     "error_code" : "APIG.3093",
     "error_msg" : "App quota c900c5612dbe451bb43cbcc49cfaf2f3 does not exist"
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
