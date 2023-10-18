:original_name: ChangeApiVersionV2.html

.. _ChangeApiVersionV2:

Switching the Version of an API
===============================

Function
--------

This API is used to switch the version of an API. A version is generated based on the current definition of an API when the API is published. The version records the definition and status of the API when it is published.

You can switch between multiple versions of an API, but only one version of an API takes effect in the same environment.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/apis/publish/{api_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                           |
   +=============+===========+========+=======================================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain a project ID, see "Appendix" > "Obtaining a Project ID" in this document. |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                                   |
   +-------------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
   | api_id      | Yes       | String | API ID.                                                                                                               |
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

   ========== ========= ====== ===============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===============
   version_id No        String API version ID.
   ========== ========= ====== ===============

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------+--------+------------------------------------------------------------+
   | Parameter    | Type   | Description                                                |
   +==============+========+============================================================+
   | publish_id   | String | Publication record ID.                                     |
   +--------------+--------+------------------------------------------------------------+
   | api_id       | String | API ID.                                                    |
   +--------------+--------+------------------------------------------------------------+
   | api_name     | String | API name.                                                  |
   +--------------+--------+------------------------------------------------------------+
   | env_id       | String | ID of the environment in which the API has been published. |
   +--------------+--------+------------------------------------------------------------+
   | remark       | String | Description about the publication.                         |
   +--------------+--------+------------------------------------------------------------+
   | publish_time | String | Publication time.                                          |
   +--------------+--------+------------------------------------------------------------+
   | version_id   | String | API version currently in use.                              |
   +--------------+--------+------------------------------------------------------------+

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
     "version_id" : "ee1a5a38d3d3493abf1dc4ed6cacfa0b"
   }

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "publish_id" : "9191cdb430724d4b8586ed7f1b962ca2",
     "api_id" : "5f918d104dc84480a75166ba99efff21",
     "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
     "version_id" : "ee1a5a38d3d3493abf1dc4ed6cacfa0b",
     "publish_time" : "2020-08-03T03:27:49.483295655Z"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2000",
     "error_msg" : "Parameter error: Serialization error: unexpected end of JSON input"
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
     "error_code" : "APIG.3022",
     "error_msg" : "The API version does not exist,id:ee1a5a38d3d3493abf1dc4ed6cacfa0b"
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
