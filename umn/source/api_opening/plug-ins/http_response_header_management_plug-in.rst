:original_name: apig-ug-0005.html

.. _apig-ug-0005:

HTTP Response Header Management Plug-in
=======================================

HTTP response headers are part of the response returned by APIG to a client that calls an API. You can customize HTTP response headers that will be contained in an API response.

.. note::

   If your gateway does not support the HTTP response header management plug-in, contact customer service to upgrade the gateway.

Usage Guidelines
----------------

You cannot modify the response headers, such as **x-apig-\*** and **x-request-id**, added by APIG, or the headers configured for CORS.

Configuration Parameters
------------------------

.. table:: **Table 1** Configuration parameters

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                              |
   +===================================+==========================================================================================================================================================================================================+
   | Name                              | Response header name, which is case-insensitive and must be unique within a plug-in. You can add a maximum of 10 response headers.                                                                       |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Value                             | Value of the response header. This parameter does not take effect and can be left blank if you set **Action** to **Delete**.                                                                             |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action                            | Response header operation. You can override, append, delete, skip, or add the specified header.                                                                                                          |
   |                                   |                                                                                                                                                                                                          |
   |                                   | **Override**                                                                                                                                                                                             |
   |                                   |                                                                                                                                                                                                          |
   |                                   | -  The value of this response header will override that of the same header that exists in an API response.                                                                                               |
   |                                   | -  If an API response contains multiple headers with the same name as the one you set here, only the value of the specified header will be returned.                                                     |
   |                                   | -  If an API response does not contain the specified header, the value you set here will be returned.                                                                                                    |
   |                                   |                                                                                                                                                                                                          |
   |                                   | **Append**                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                          |
   |                                   | -  If an API response contains the specified header, the value you set here will be added, following the existing value. The two values will be separated with commas (,).                               |
   |                                   | -  If an API response contains multiple headers with the same name as the one you set here, values of these headers will be separated with commas (,) and followed by the value of the specified header. |
   |                                   | -  If an API response does not contain the specified header, the value you set here will be returned.                                                                                                    |
   |                                   |                                                                                                                                                                                                          |
   |                                   | **Delete**                                                                                                                                                                                               |
   |                                   |                                                                                                                                                                                                          |
   |                                   | -  If an API response contains the specified header, the header will be deleted.                                                                                                                         |
   |                                   | -  If an API response contains multiple headers with the same name as the one you set here, all these headers will be deleted.                                                                           |
   |                                   |                                                                                                                                                                                                          |
   |                                   | **Skip**                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                          |
   |                                   | -  If an API response contains the specified header, the header will be skipped.                                                                                                                         |
   |                                   | -  If an API response contains multiple headers with the same name as the one you set here, values of all these headers will be returned without modification.                                           |
   |                                   | -  If an API response does not contain the specified header, the value you set here will be returned.                                                                                                    |
   |                                   |                                                                                                                                                                                                          |
   |                                   | **Add**                                                                                                                                                                                                  |
   |                                   |                                                                                                                                                                                                          |
   |                                   | The value of the specified header will be returned even if the header does not exist in an API response.                                                                                                 |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Script
--------------

.. code-block::

   {
       "response_headers": [
           {
               "name": "test",
               "value": "test",
               "action": "append"
           },
           {
               "name": "test1",
               "value": "test1",
               "action": "override"
           }
       ]
   }
