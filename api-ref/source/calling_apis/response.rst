:original_name: apig-api-190529269.html

.. _apig-api-190529269:

Response
========

Status Code
-----------

After sending a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits, ranging from 1xx to 5xx. It indicates the status of a request. For more information, see :ref:`HTTP Status Codes <apig-en-api-180713206>`.

For example, if status code **201** is returned for calling the API used to create an API group (dedicated gateways), the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

(Optional) Response Body
------------------------

The body of a response is often returned in structured format as specified in the **Content-Type** header field. The response body transfers content except the response header.

The following is part of the response body for the API used to create an API group (dedicated gateways).

.. code-block::

   {
       "id": "abcdef...",
       "name": "APIGroup_test",
       "remark": "api group remark",
   ......
   }

If an error occurs during API calling, an error code and a message will be displayed. The following shows an error response body.

.. code-block::

   {
       "error_msg": "The token is missing.",
       "error_code": "APIG.1000"
   }

In the response body, **error_code** is an error code, and **error_msg** provides information about the error.
