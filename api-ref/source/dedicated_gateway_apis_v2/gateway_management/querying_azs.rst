:original_name: ListAvailableZonesV2.html

.. _ListAvailableZonesV2:

Querying AZs
============

Function
--------

This API is used to query AZs where you can buy gateways.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/available-zones

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

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

   +-----------------+--------------------------------------------------------------------------------------+-------------+
   | Parameter       | Type                                                                                 | Description |
   +=================+======================================================================================+=============+
   | available_zones | Array of :ref:`AvailableZone <listavailablezonesv2__response_availablezone>` objects | AZ list.    |
   +-----------------+--------------------------------------------------------------------------------------+-------------+

.. _listavailablezonesv2__response_availablezone:

.. table:: **Table 4** AvailableZone

   +------------+--------------------------------------------------------------------+---------------------------------------+
   | Parameter  | Type                                                               | Description                           |
   +============+====================================================================+=======================================+
   | name       | String                                                             | AZ name.                              |
   +------------+--------------------------------------------------------------------+---------------------------------------+
   | id         | String                                                             | Error message.                        |
   +------------+--------------------------------------------------------------------+---------------------------------------+
   | code       | String                                                             | AZ code.                              |
   +------------+--------------------------------------------------------------------+---------------------------------------+
   | port       | String                                                             | AZ port.                              |
   +------------+--------------------------------------------------------------------+---------------------------------------+
   | local_name | :ref:`LocalName <listavailablezonesv2__response_localname>` object | AZ names.                             |
   +------------+--------------------------------------------------------------------+---------------------------------------+
   | specs      | Map<String,Boolean>                                                | Gateway editions available in the AZ. |
   +------------+--------------------------------------------------------------------+---------------------------------------+

.. _listavailablezonesv2__response_localname:

.. table:: **Table 5** LocalName

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   en_us     String AZ name.
   zh_cn     String AZ name.
   ========= ====== ===========

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
     "available_zones" : [ {
       "code" : "xx-xxx-4a",
       "id" : "effdcbc7d4d64a02aa1fa26b42f56533",
       "local_name" : {
         "en_us" : "AZ1",
         "zh_cn" : "<Name_of_AZ1>"
       },
       "name" : "<Name_of_AZ1>",
       "port" : "8403",
       "specs" : {
         "BASIC" : true,
         "ENTERPRISE" : true,
         "PLATINUM" : true,
         "PROFESSIONAL" : true,
       }
     }, {
       "code" : "xx-xxx-4b",
       "id" : "a0865121f83b41cbafce65930a22a6e8",
       "local_name" : {
         "en_us" : "AZ2",
         "zh_cn" : "<Name_of_AZ2>"
       },
       "name" : "<Name_of_AZ2>",
       "port" : "8404",
       "specs" : {
         "BASIC" : true,
         "ENTERPRISE" : true,
         "PLATINUM" : true,
         "PROFESSIONAL" : true,
       }
     } ]
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "APIC.7102",
     "error_msg" : "Incorrect token or token resolution failed"
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "APIC.7106",
     "error_msg" : "No permissions to request for the method"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIC.9000",
     "error_msg" : "Failed to request internal service"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
