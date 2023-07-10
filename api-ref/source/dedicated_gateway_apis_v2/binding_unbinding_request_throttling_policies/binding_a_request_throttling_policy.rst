:original_name: AssociateRequestThrottlingPolicyV2.html

.. _AssociateRequestThrottlingPolicyV2:

Binding a Request Throttling Policy
===================================

Function
--------

The request throttling policy bound to an API will control access of all users to the API.If the number of API calls within a specified period reaches the limit, subsequent access will be rejected, protecting the backend API from abnormal traffic and ensuring stable service running.This API is used to bind a request throttling policy to an API that has been published in an environment. You can bind different request throttling policies to an API in different environments, but can bind only one request throttling policy to the API in each environment.

URI
---

POST /v2/{project_id}/apigw/instances/{instance_id}/throttle-bindings

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

   +-----------------+-----------------+------------------+-------------------------------+
   | Parameter       | Mandatory       | Type             | Description                   |
   +=================+=================+==================+===============================+
   | strategy_id     | Yes             | String           | Request throttling policy ID. |
   |                 |                 |                  |                               |
   |                 |                 |                  | Minimum: **1**                |
   |                 |                 |                  |                               |
   |                 |                 |                  | Maximum: **65**               |
   +-----------------+-----------------+------------------+-------------------------------+
   | publish_ids     | Yes             | Array of strings | API publication record ID.    |
   +-----------------+-----------------+------------------+-------------------------------+

Response Parameters
-------------------

**Status code: 201**

.. table:: **Table 4** Response body parameters

   +-----------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter       | Type                                                                                                         | Description                                |
   +=================+==============================================================================================================+============================================+
   | throttle_applys | Array of :ref:`ThrottleApiBinding <associaterequestthrottlingpolicyv2__response_throttleapibinding>` objects | Request throttling policy binding records. |
   +-----------------+--------------------------------------------------------------------------------------------------------------+--------------------------------------------+

.. _associaterequestthrottlingpolicyv2__response_throttleapibinding:

.. table:: **Table 5** ThrottleApiBinding

   +-----------------------+-----------------------+-----------------------------------+
   | Parameter             | Type                  | Description                       |
   +=======================+=======================+===================================+
   | publish_id            | String                | API publication record ID.        |
   +-----------------------+-----------------------+-----------------------------------+
   | scope                 | Integer               | Scope of the policy.              |
   |                       |                       |                                   |
   |                       |                       | -  1: the API                     |
   |                       |                       |                                   |
   |                       |                       | -  2: a user                      |
   |                       |                       |                                   |
   |                       |                       | -  3: an app                      |
   |                       |                       |                                   |
   |                       |                       | Currently, only "1" is supported. |
   |                       |                       |                                   |
   |                       |                       | Enumeration values:               |
   |                       |                       |                                   |
   |                       |                       | -  **1**                          |
   |                       |                       |                                   |
   |                       |                       | -  **2**                          |
   |                       |                       |                                   |
   |                       |                       | -  **3**                          |
   +-----------------------+-----------------------+-----------------------------------+
   | strategy_id           | String                | Request throttling policy ID.     |
   +-----------------------+-----------------------+-----------------------------------+
   | apply_time            | String                | Binding time.                     |
   +-----------------------+-----------------------+-----------------------------------+
   | id                    | String                | Binding record ID.                |
   +-----------------------+-----------------------+-----------------------------------+

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
     "publish_ids" : [ "40e7162dc6b94bbbbb1a60d2a24b1b0c" ],
     "strategy_id" : "3437448ad06f4e0c91a224183116e965"
   }

Example Responses
-----------------

**Status code: 201**

Created

.. code-block::

   {
     "throttle_applys" : [ {
       "publish_id" : "40e7162dc6b94bbbbb1a60d2a24b1b0c",
       "scope" : 1,
       "strategy_id" : "3437448ad06f4e0c91a224183116e965",
       "apply_time" : "2020-08-03T12:25:52.257613934Z",
       "id" : "3e06ac135e18477e918060d3c59d6f6a"
     } ]
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
     "error_code" : "APIG.3005",
     "error_msg" : "Request throttling policy 3437448ad06f4e0c91a224183116e965 does not exist"
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
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
