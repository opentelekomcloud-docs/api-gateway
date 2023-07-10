:original_name: AssociateCertificateV2.html

.. _AssociateCertificateV2:

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

.. code-block::

   {
     "name" : "cert_demo",
     "private_key" : "'-----BEGIN CERTIFICATE-----\\nMIIEcDCCAtigAwIBAgIRAKUYqTtQbsPhVauuteGD8kMwDQYJKoZIhvcNAQELBQAw\\ngZMxHjAcBgNVBAoTFW1rY2VydCBkZXZlbG9wbWVudCBDQTE0MDIGA1UECwwrQ0hJ\\nTkFcbDAwNDk1MzA1QERFU0tUT1AtTDJURk9GSCAobGl1cnVpeHVlKTE7MDkGA1UE\\nAwwybWtjZXJ0IENISU5BXGwwMDQ5NTMwNUBERVNLVE9QLUwyVEZPRkggKGxpdXJ1\\naXh1ZSkwHhcNMTkwNjAxMDAwMDAwWhcNMzAwODA0MDc0MTE5WjBfMScwJQYDVQQK\\nEx5ta2NlcnQgZGV2ZWxvcG1lbnQgY2VydGlmaWNhdGUxNDAyBgNVBAsMK0NISU5B\\nXGwwMDQ5NTMwNUBERVNLVE9QLUwyVEZPRkggKGxpdXJ1aXh1ZSkwggEiMA0GCSqG\\nSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDYvPx9H8ZY9iUf5A8hT8s/gTThEOa3nswW\\njxxU58+dIiwvzdIioc+CaggMz/rjT3bt9jRilKvzkJjryUxLNOe3JsdJogm0OSxc\\nSJWOhdZd/vScImWajM5t3M/M7xgt1g813PNEVJ/uTaEwm6K3sAlqGJfgiU/ep6pb\\nI4S9i1c3VYLTfGF2ND5kTaysp69/mXl4IUDWn82n0TpjB4BvoiYD9ORMcvBBGCBh\\nnU2x497Uyo0X/MkreoxLxLEO2s4/TZfpZ0Ezsi/yHwjTRQ0ut53IKbSZDoBf3HLE\\nPw1Y4q2s4qjN6ImZmkYX+Qvx5MxdHCNsfPsDFTYX2rl+vCpqtDW/AgMBAAGjcjBw\\nMA4GA1UdDwEB/wQEAwIFoDATBgNVHSUEDDAKBggrBgEFBQcDATAMBgNVHRMBAf8E\\nAjAAMB8GA1UdIwQYMBaAFEV9QNgV6FDCbMBoI4uT/JL/8ZHjMBoGA1UdEQQTMBGC\\nD3d3dy5jb21wYW55LmNvbTANBgkqhkiG9w0BAQsFAAOCAYEAXkrRlJ2z0xEGBiE3\\ncvGtePxERVm0cdU1fI7qoQRd8bg0KJwvCvFfJZoCWD41saZnXcfwn+1eAD6txWsV\\nkgq784DeTltqC5tU6l6kpXyU1lkTm9U7/Qbb8QGB8GaRAP9VJTLfOzjieZrj/55L\\nyrSkK84hvo6XSaEhqaBUWQN1qr8MY9/P0sZ2H0S9uu3Ezu9r/jx849aYDKeN4Zdf\\nxda1iXz+6UYUQKo5cveGKu+HmIW5V+sVVUfBCbr1FrUgaSbeZDnKdm6xlQZ70los\\nn4yLrpdbL0r5x41es94PaLSZC9+UANLf7fqGKpYlYdUU3YigUs3ed9Cn1f1ScI6V\\nJgR5tyK0dAb1n5tJwM2FA0cu56L3h2h71Jxgs4mEvBlqy+h6wVOIboj4UzQRnm+t\\n1Um4rYopw240iy4oRTYqB3dcsA3y3KYcTzA+LCUOcnWcaZSFiL9kEKqCWljZs51A\\nuux1UisF8p/iMNyZPoPYIBQnO+oN2GJ72krI2pmMJgEkag38\\n-----END CERTIFICATE-----\\n'",
     "cert_content" : "'-----BEGIN PRIVATE KEY-----\\nMIIEvQIBADANBgkqhkiG9w0BAQEFAASCBKcwggSjAgEAAoIBAQDYvPx9H8ZY9iUf\\n5A8hT8s/gTThEOa3nswWjxxU58+dIiwvzdIioc+CaggMz/rjT3bt9jRilKvzkJjr\\nyUxLNOe3JsdJogm0OSxcSJWOhdZd/vScImWajM5t3M/M7xgt1g813PNEVJ/uTaEw\\nm6K3sAlqGJfgiU/ep6pbI4S9i1c3VYLTfGF2ND5kTaysp69/mXl4IUDWn82n0Tpj\\nB4BvoiYD9ORMcvBBGCBhnU2x497Uyo0X/MkreoxLxLEO2s4/TZfpZ0Ezsi/yHwjT\\nRQ0ut53IKbSZDoBf3HLEPw1Y4q2s4qjN6ImZmkYX+Qvx5MxdHCNsfPsDFTYX2rl+\\nvCpqtDW/AgMBAAECggEBAMJGvOiHp+qsUODCM5G/jcdR0Q2Bcd3b+MKr61BsLdyC\\n+iqripXCh1g2JRse/pvs6gUpsRFAhNWhooGQAdRUCvRQTUjCd4JV0V6zLWQAsgO1\\nepvN9VdQqeUujhH7q6fCfgXhFSoF1QnuCfOhPnz6zaWNf+4kBzTlA74IG38vvLD6\\nTccgvXNrJEWMM+AN6uCndEMkPG2VtCor9VDaN5iuBN9NsAxTGZu9wgrZzg1W0rVZ\\nC/Psh2U2gwXHBzsiygB3n08R+7MSwulpsvUone2E4IT+VDURWIIIcVQZtT6SxuRt\\npFEy7E/PfKV1VRvEvyGtZSSLkt0WxqHPENrj3LuW77kCgYEA4X+iRh6jTSmJ1fHl\\n0qhCSFWXjp1B+cajNs62N2kFcRkOtD5BvWihlDbuLaq/eYfErKET6Z8jnbRyQCJV\\n/ePqRIZ30gjTPRr55X8ZXb+hCficHnK5LZah6HwyRL337FzejTxs3J7C1rVmYq/n\\nCjfa3bJQ6zUtxRO+B2BlCgES9q0CgYEA9g4ByVyydao8ZEC9Qbn9Pzd/LsIbBOAG\\nPg7Ib0vwHyRv9oPHTc7dla+YBTfNVuFOt2e/KKf0meZnM6OiW/r38zgwLMwzHHcs\\nryMNGgwffSwmDXgrswkXu5ICuoc1+2s3GGNFkjg7IrfcHlEpVAn/ttJTCmbvTMGo\\nHM+oJPpGp5sCgYAopHx27ua37ZiuOt8VTMZFi0e5qJZPkoGwSymEayVT8RQ5YE8w\\n+D7HG+9pw7CnEtVb19xi6w/cSL2e2ZFuJToAB8xoyrZn+Qi5WGMWBofb6DcbNcoy\\ncUfVQy08PpEExOhHxHBKg0LSt/cwKkwWB2MnOhBjlD4fmyNQ6QrM9syYMQKBgH+8\\nv9Kwq/kH+rg1H8uKad2yyvUUUgCS6Mq40/drneoc+X8p5IMRXNnDwhEbah+rcjkm\\nxAewQfzPr04Qqk5EGQsMZX4sOHCTsf/uG3QlTQenrs2ZUF5u3wJCh+YcIbs3au/f\\nQZPqW1Dn0H9wtRrq4fUgdXnV/G+FreffKjSgNaP3AoGAT8wX6ZszA5HrIGSo4pi7\\nDnbMNuYe1cpcyoAi178YVklom6uGutIiafngapViESKZ0Y8X/lYzU6ELclimqJPB\\nXD4nSD64YVvi+TjzwLK61tEUuAnYlWrtXQORWPQ5tHGlhCZPrciO2QH5P9cxoU3Z\\npGfmyACUF4Od9tdq4t4S9j4=\\n-----END PRIVATE KEY-----\\n'"
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
