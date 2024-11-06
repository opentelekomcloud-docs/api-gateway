:original_name: BatchDisassociateDomainsV2.html

.. _BatchDisassociateDomainsV2:

Unbinding an SSL Certificate from a Domain Name
===============================================

Function
--------

This API is used to unbind an SSL certificate from a domain name.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

POST /v2/{project_id}/apigw/certificates/{certificate_id}/domains/detach

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

   +-----------+-----------+-----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+
   | Parameter | Mandatory | Type                                                                                                            | Description                                               |
   +===========+===========+=================================================================================================================+===========================================================+
   | domains   | Yes       | Array of :ref:`AttachOrDetachDomainInfo <batchdisassociatedomainsv2__request_attachordetachdomaininfo>` objects | Domain names the certificate is bound to or unbound from. |
   +-----------+-----------+-----------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------+

.. _batchdisassociatedomainsv2__request_attachordetachdomaininfo:

.. table:: **Table 4** AttachOrDetachDomainInfo

   +-------------------------------------+-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                           | Mandatory | Type             | Description                                                                                                                                            |
   +=====================================+===========+==================+========================================================================================================================================================+
   | domain                              | Yes       | String           | Domain name.                                                                                                                                           |
   +-------------------------------------+-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_ids                        | No        | Array of strings | Gateway IDs.                                                                                                                                           |
   +-------------------------------------+-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | verified_client_certificate_enabled | No        | Boolean          | Whether to enable client certificate verification. It is enabled by default if trusted_root_ca exists, and disabled if trusted_root_ca does not exist. |
   +-------------------------------------+-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

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

Unbinding an SSL certificate from a domain name

.. code-block::

   {
     "domains" : [ {
       "domain" : "apigtest.example.com",
       "instance_ids" : [ "f0fa1789-3b76-433b-a787-9892951c620e", "7d39549681c54d968ec2910da9da95cd" ]
     } ]
   }

Example Responses
-----------------

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
204         OK
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
