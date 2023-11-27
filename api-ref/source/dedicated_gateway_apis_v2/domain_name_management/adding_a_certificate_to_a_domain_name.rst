:original_name: AssociateCertificateV2_1.html

.. _AssociateCertificateV2_1:

Adding a Certificate to a Domain Name
=====================================

Function
--------

When you create an API to be accessed through HTTPS, you must add an SSL certificate to the independent domain name that has been bound to the group the API belongs to.

This API is used to add a certificate to a specific domain name.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/domains/{domain_id}/certificate

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | group_id    | Yes       | String | API group ID.                                                                                           |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | domain_id   | Yes       | String | Domain ID.                                                                                              |
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

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================+
   | cert_content | Yes       | String | Certificate content.                                                                                                                |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | name         | Yes       | String | Certificate name. It can contain 4 to 50 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+
   | private_key  | Yes       | String | Private key.                                                                                                                        |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                           | Type                  | Description                                                                                                                                                                                                          |
   +=====================================+=======================+======================================================================================================================================================================================================================+
   | url_domain                          | String                | Custom domain name.                                                                                                                                                                                                  |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                                  | String                | Domain ID.                                                                                                                                                                                                           |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                              | Integer               | CNAME resolution status.                                                                                                                                                                                             |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  1: not resolved                                                                                                                                                                                                   |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  2: resolving                                                                                                                                                                                                      |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  3: resolved                                                                                                                                                                                                       |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  4: resolution failed                                                                                                                                                                                              |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | Enumeration values:                                                                                                                                                                                                  |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  **1**                                                                                                                                                                                                             |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  **2**                                                                                                                                                                                                             |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  **3**                                                                                                                                                                                                             |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | -  **4**                                                                                                                                                                                                             |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | min_ssl_version                     | String                | Minimum SSL version supported.                                                                                                                                                                                       |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_http_redirect_to_https           | Boolean               | Whether to enable HTTP redirection to HTTPS. The value false means disable and true means enable. The default value is false.                                                                                        |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | Default: **false**                                                                                                                                                                                                   |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | verified_client_certificate_enabled | Boolean               | Whether to enable client certificate verification. This parameter is available only when a certificate is bound. It is enabled by default if trusted_root_ca exists, and disabled if trusted_root_ca does not exist. |
   |                                     |                       |                                                                                                                                                                                                                      |
   |                                     |                       | Default: **false**                                                                                                                                                                                                   |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ssl_name                            | String                | Certificate name.                                                                                                                                                                                                    |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ssl_id                              | String                | Certificate ID.                                                                                                                                                                                                      |
   +-------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

Binding a certificate to a domain name

.. code-block::

   {
     "name" : "cert_demo",
     "private_key" : "'-----BEGIN PRIVATE KEY-----THIS IS YOUR PRIVATE KEY-----END PRIVATE KEY-----\\n'",
     "cert_content" : "'-----BEGIN CERTIFICATE-----THIS IS YOUR CERT CONTENT-----END CERTIFICATE-----\\n'"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "ssl_name" : "cert_demo",
     "url_domain" : "www.example.com",
     "ssl_id" : "a27be832f2e9441c8127fe48e3b5ac67",
     "id" : " f6bb84ccf1c34035878aa51b7253b21c",
     "status" : 3
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
     "error_code" : "APIG.3020",
     "error_msg" : "The URL domain does not exist"
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
