:original_name: apig-api-190529269.html

.. _apig-api-190529269:

Response
========

After sending a request, you will receive a response, including a status code, response header, and response body.

Status Code
-----------

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request. For more information, see :ref:`HTTP Status Codes <apig-api-180713206>`.

For example, if status code **201** is returned for calling the API used to create an API group, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

For example, when calling the API used to create an API group (dedicated gateways), the response headers are shown below.


.. figure:: /_static/images/en-us_image_0000001892790552.png
   :alt: **Figure 1** Response headers for creating an API group

   **Figure 1** Response headers for creating an API group

Response Body
-------------

The body of a response is often returned in structured format as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to create an API group.

.. code-block::

   {
    "id": "41e08fbaca9f4d64bde467d0dd89ff51",
    "name": "aaa",
    "status": 1,
    "sl_domain": "41e08fbaca9f4d64bde467d0dd89ff51.example.cloudapis.com",
    "register_time": "2024-05-23T08:03:56.419897855Z",
    "update_time": "2024-05-23T08:03:56.419897962Z",
    "on_sell_status": 2,
    "url_domains": [],
    "sl_domain_access_enabled": true,
    "sl_domains": [
     "41e08fbaca9f4d64bde467d0dd89ff51.example.cloudapis.com"
    ],
    "remark": "",
    "call_limits": 0,
    "time_interval": 0,
    "time_unit": "",
    "is_default": 2,
    "version": "",
   }

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block::

   {
       "error_msg": "The token is missing.",
       "error_code": "APIG.1000"
   }

In the response body, **error_code** is an error code, and **error_msg** provides information about the error.
