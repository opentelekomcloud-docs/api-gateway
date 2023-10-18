:original_name: UpdateDomainV2.html

.. _UpdateDomainV2:

Modifying a Domain Name
=======================

Function
--------

This API is used to modify the configuration of a domain name bound to an API group.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/domains/{domain_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | group_id    | Yes       | String | API group ID.                                                                                                         |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | domain_id   | Yes       | String | Domain ID.                                                                                                            |
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

   +-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                           | Mandatory       | Type            | Description                                                                                                                                                                                                          |
   +=====================================+=================+=================+======================================================================================================================================================================================================================+
   | min_ssl_version                     | Yes             | String          | Minimum SSL version. TLS 1.1 and TLS 1.2 are supported.                                                                                                                                                              |
   |                                     |                 |                 |                                                                                                                                                                                                                      |
   |                                     |                 |                 | Default: **TLSv1.1**                                                                                                                                                                                                 |
   |                                     |                 |                 |                                                                                                                                                                                                                      |
   |                                     |                 |                 | Enumeration values:                                                                                                                                                                                                  |
   |                                     |                 |                 |                                                                                                                                                                                                                      |
   |                                     |                 |                 | -  **TLSv1.1**                                                                                                                                                                                                       |
   |                                     |                 |                 |                                                                                                                                                                                                                      |
   |                                     |                 |                 | -  **TLSv1.2**                                                                                                                                                                                                       |
   +-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_http_redirect_to_https           | No              | Boolean         | Whether to enable HTTP redirection to HTTPS. The value false means disable and true means enable. The default value is false.                                                                                        |
   |                                     |                 |                 |                                                                                                                                                                                                                      |
   |                                     |                 |                 | Default: **false**                                                                                                                                                                                                   |
   +-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | verified_client_certificate_enabled | No              | Boolean         | Whether to enable client certificate verification. This parameter is available only when a certificate is bound. It is enabled by default if trusted_root_ca exists, and disabled if trusted_root_ca does not exist. |
   |                                     |                 |                 |                                                                                                                                                                                                                      |
   |                                     |                 |                 | Default: **false**                                                                                                                                                                                                   |
   +-------------------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
     "min_ssl_version" : "TLSv1.2"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "id" : "0a515af69f4e4dcca84fbf85f68c0e27",
     "url_domain" : "www.example.com",
     "status" : 3,
     "min_ssl_version" : "TLSv1.2",
     "is_http_redirect_to_https" : false,
     "verified_client_certificate_enabled" : false
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3474",
     "error_msg" : "The API group ID in the URL does not match the API group to which the URL domain has been bound"
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
