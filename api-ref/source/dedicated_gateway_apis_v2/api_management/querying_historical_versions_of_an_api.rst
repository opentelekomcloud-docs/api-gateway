:original_name: ListApiVersionsV2.html

.. _ListApiVersionsV2:

Querying Historical Versions of an API
======================================

Function
--------

This API is used to query the historical versions of an API. APIG retains a maximum of 10 historical versions for each API in an environment.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/apis/publish/{api_id}

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
   | env_id          | No              | String          | Environment ID.                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | env_name        | No              | String          | Environment name.                                                                                                                                                                   |
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

   +--------------+-------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter    | Type                                                                                | Description                                          |
   +==============+=====================================================================================+======================================================+
   | size         | Integer                                                                             | Length of the returned resource list.                |
   +--------------+-------------------------------------------------------------------------------------+------------------------------------------------------+
   | total        | Long                                                                                | Number of resources that match the query conditions. |
   +--------------+-------------------------------------------------------------------------------------+------------------------------------------------------+
   | api_versions | Array of :ref:`ApiVersionResp <listapiversionsv2__response_apiversionresp>` objects | Historical version list.                             |
   +--------------+-------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listapiversionsv2__response_apiversionresp:

.. table:: **Table 5** ApiVersionResp

   +-----------------------+-----------------------+--------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                  |
   +=======================+=======================+==============================================================+
   | version_id            | String                | API version ID.                                              |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | version_no            | String                | API version.                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | api_id                | String                | API ID.                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | env_id                | String                | ID of the environment in which the API has been published.   |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | env_name              | String                | Name of the environment in which the API has been published. |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | remark                | String                | Description about the publication.                           |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | publish_time          | String                | Publication time.                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | status                | Integer               | Version status.                                              |
   |                       |                       |                                                              |
   |                       |                       | -  1: effective                                              |
   |                       |                       |                                                              |
   |                       |                       | -  2: not effective                                          |
   |                       |                       |                                                              |
   |                       |                       | Enumeration values:                                          |
   |                       |                       |                                                              |
   |                       |                       | -  **1**                                                     |
   |                       |                       |                                                              |
   |                       |                       | -  **2**                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------+

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
     "api_versions" : [ {
       "version_id" : "ee1a5a38d3d3493abf1dc4ed6cacfa0b",
       "version_no" : "20200803093600",
       "api_id" : "5f918d104dc84480a75166ba99efff21",
       "env_id" : "DEFAULT_ENVIRONMENT_RELEASE_ID",
       "env_name" : "RELEASE",
       "publish_time" : "2020-08-03T01:36:00Z",
       "status" : 1
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2012",
     "error_msg" : "Invalid parameter value,parameterName:env_name. Please refer to the support documentation"
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
