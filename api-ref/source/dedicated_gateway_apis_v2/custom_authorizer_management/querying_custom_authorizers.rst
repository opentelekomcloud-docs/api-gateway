:original_name: ListCustomAuthorizersV2.html

.. _ListCustomAuthorizersV2:

Querying Custom Authorizers
===========================

Function
--------

This API is used to query all the custom authorizers under a gateway.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances/{instance_id}/authorizers

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

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
   | id              | No              | String          | ID.                                                                                                                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | No              | String          | Name.                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | Type.                                                                                                                                                                               |
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

   +-----------------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter       | Type                                                                                      | Description                                          |
   +=================+===========================================================================================+======================================================+
   | size            | Integer                                                                                   | Length of the returned resource list.                |
   +-----------------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | total           | Long                                                                                      | Number of resources that match the query conditions. |
   +-----------------+-------------------------------------------------------------------------------------------+------------------------------------------------------+
   | authorizer_list | Array of :ref:`AuthorizerResp <listcustomauthorizersv2__response_authorizerresp>` objects | Custom authorizers.                                  |
   +-----------------+-------------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listcustomauthorizersv2__response_authorizerresp:

.. table:: **Table 5** AuthorizerResp

   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                          | Description                                                                                                       |
   +=======================+===============================================================================+===================================================================================================================+
   | name                  | String                                                                        | Custom authorizer name.                                                                                           |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | It can contain 3 to 64 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed. |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | type                  | String                                                                        | Custom authorizer type.                                                                                           |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  FRONTEND                                                                                                       |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  BACKEND                                                                                                        |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Modification is not allowed.                                                                                      |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Enumeration values:                                                                                               |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  **FRONTEND**                                                                                                   |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  **BACKEND**                                                                                                    |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | authorizer_type       | String                                                                        | Value: FUNC.                                                                                                      |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Enumeration values:                                                                                               |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  **FUNC**                                                                                                       |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | authorizer_uri        | String                                                                        | Function URN.                                                                                                     |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | network_type          | String                                                                        | Function network architecture:                                                                                    |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  V1: non-VPC                                                                                                    |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  V2: VPC                                                                                                        |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Default: **V1**                                                                                                   |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Enumeration values:                                                                                               |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  **V1**                                                                                                         |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | -  **V2**                                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | authorizer_version    | String                                                                        | Function version.                                                                                                 |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | If both a function alias URN and version are passed, the alias URN will be used and the version will be ignored.  |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Maximum: **64**                                                                                                   |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | authorizer_alias_uri  | String                                                                        | Function alias URN.                                                                                               |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | If both a function alias URN and version are passed, the alias URN will be used and the version will be ignored.  |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | identities            | Array of :ref:`Identity <listcustomauthorizersv2__response_identity>` objects | Identity source.                                                                                                  |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | ttl                   | Integer                                                                       | Maximum cache age.                                                                                                |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | user_data             | String                                                                        | User data.                                                                                                        |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | ld_api_id             | String                                                                        | Custom backend ID.                                                                                                |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Currently, this parameter is not supported.                                                                       |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | need_body             | Boolean                                                                       | Indicates whether to send the body.                                                                               |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | id                    | String                                                                        | Custom authorizer ID.                                                                                             |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                                                                        | Creation time.                                                                                                    |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | roma_app_id           | String                                                                        | ID of the application to which the custom authorizer belongs.                                                     |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Currently, this parameter is not supported.                                                                       |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | roma_app_name         | String                                                                        | Name of the application to which the custom authorizer belongs.                                                   |
   |                       |                                                                               |                                                                                                                   |
   |                       |                                                                               | Currently, this parameter is not supported.                                                                       |
   +-----------------------+-------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

.. _listcustomauthorizersv2__response_identity:

.. table:: **Table 6** Identity

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                 |
   +=======================+=======================+=============================================================================================================+
   | name                  | String                | Parameter name.                                                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------+
   | location              | String                | Parameter location.                                                                                         |
   |                       |                       |                                                                                                             |
   |                       |                       | Enumeration values:                                                                                         |
   |                       |                       |                                                                                                             |
   |                       |                       | -  **HEADER**                                                                                               |
   |                       |                       |                                                                                                             |
   |                       |                       | -  **QUERY**                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------+
   | validation            | String                | Parameter verification expression. The default value is null, indicating that no verification is performed. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

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
     "authorizer_list" : [ {
       "name" : "Authorizer_demo",
       "type" : "FRONTEND",
       "authorizer_type" : "FUNC",
       "authorizer_uri" : "urn:fss:xx-xxx-4:106506b9a92342df9a5025fc12351cfc:function:defau:apigDemo_1592617458814",
       "network_type" : "V1",
       "authorizer_version" : "v1",
       "authorizer_alias_uri" : "urn:fss:xx-xxx-4:106506b9a92342df9a5025fc12351cfc:function:defau:apigDemo_1592617458814:!v1",
       "identities" : [ {
         "name" : "header",
         "location" : "HEADER"
       } ],
       "ttl" : 0,
       "user_data" : "authorizer_test",
       "id" : "0d982c1ac3da493dae47627b6439fc5c",
       "create_time" : "2020-07-31T11:55:43Z"
     } ]
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.2011",
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
     "error_code" : "APIG.3030",
     "error_msg" : "The instance does not exist;id:eddc4d25480b4cd6b512f270a1b8b341"
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
