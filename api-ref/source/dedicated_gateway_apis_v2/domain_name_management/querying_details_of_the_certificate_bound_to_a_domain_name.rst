:original_name: ShowDetailsOfDomainNameCertificateV2.html

.. _ShowDetailsOfDomainNameCertificateV2:

Querying Details of the Certificate Bound to a Domain Name
==========================================================

Function
--------

This API is used to query the details of the certificate bound to a domain name.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/api-groups/{group_id}/domains/{domain_id}/certificate/{certificate_id}

.. table:: **Table 1** Path Parameters

   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Mandatory | Type   | Description                                                                                                           |
   +================+===========+========+=======================================================================================================================+
   | project_id     | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id    | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | group_id       | Yes       | String | API group ID.                                                                                                         |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | domain_id      | Yes       | String | Domain ID.                                                                                                            |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | certificate_id | Yes       | String | Certificate ID.                                                                                                       |
   +----------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------+
   | Parameter             | Type                  | Description                                               |
   +=======================+=======================+===========================================================+
   | id                    | String                | Certificate ID.                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | name                  | String                | Certificate name.                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | type                  | String                | Certificate type. Options:                                |
   |                       |                       |                                                           |
   |                       |                       | -  global: Global certificate.                            |
   |                       |                       |                                                           |
   |                       |                       | -  instance: Gateway certificate.                         |
   |                       |                       |                                                           |
   |                       |                       | Enumeration values:                                       |
   |                       |                       |                                                           |
   |                       |                       | -  **global**                                             |
   |                       |                       |                                                           |
   |                       |                       | -  **instance**                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | instance_id           | String                | Gateway ID.                                               |
   |                       |                       |                                                           |
   |                       |                       | -  If type is set to global, the default value is common. |
   |                       |                       |                                                           |
   |                       |                       | -  If type is set to instance, a gateway ID is displayed. |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | project_id            | String                | Project ID.                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | create_time           | String                | Creation time.                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | update_time           | String                | Update time.                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | common_name           | String                | Certificate domain name.                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | san                   | Array of strings      | Subject alternative names.                                |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | version               | Integer               | Certificate version.                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | organization          | Array of strings      | Company or organization.                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | organizational_unit   | Array of strings      | Department.                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | locality              | Array of strings      | City.                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | state                 | Array of strings      | State or province.                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | country               | Array of strings      | Country or region.                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | not_before            | String                | Start time of the certificate validity period.            |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | not_after             | String                | End time of the certificate validity period.              |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | serial_number         | String                | Serial No.                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | issuer                | Array of strings      | Certificate issuer.                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------+
   | signature_algorithm   | String                | Signature algorithm.                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "serial_number" : "219450666855693268010130472645821723203",
     "version" : 3,
     "san" : [ "www.company.com" ],
     "not_before" : "2019-06-01T00:00:00Z",
     "issuer" : [ "mkcert development CA" ],
     "not_after" : "2030-08-04T07:41:19Z",
     "organization" : [ "mkcert development certificate" ],
     "signature_algorithm" : "SHA256-RSA",
     "organizational_unit" : [ "XXX\\\\DESKTOP-L2TFOFH" ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:domain_id. Please refer to the support documentation"
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
