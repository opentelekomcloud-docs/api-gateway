:original_name: apig_03_0022.html

.. _apig_03_0022:

HTTP Response Header Management
===============================

HTTP response headers are part of the response returned by APIG to a client that calls an API. You can customize HTTP response headers that will be contained in an API response.

.. note::

   If your gateway does not support this policy, contact technical support to upgrade the gateway to the latest version.

Usage Guidelines
----------------

-  You have understood the :ref:`guidelines for policy creation and API binding <apig_03_0019__en-us_topic_0000001221774151_en-us_topic_0000001151883501_section126118109015>`.
-  You cannot modify the response headers (including **x-apig-\*** and **x-request-id**) added by APIG or the headers required for CORS.

Configuration Parameters
------------------------

.. table:: **Table 1** Configuration parameters

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                  |
   +===================================+==============================================================================================================================================================================================================+
   | Name                              | Response header name, which is case-insensitive and must be unique within a plug-in. You can add a maximum of 10 response headers.                                                                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Value                             | Value of the response header. This parameter does not take effect and can be left blank if you set **Action** to **Delete**.                                                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Action                            | Response header operation. You can override, append, delete, skip, or add response headers.                                                                                                                  |
   |                                   |                                                                                                                                                                                                              |
   |                                   | **Override**                                                                                                                                                                                                 |
   |                                   |                                                                                                                                                                                                              |
   |                                   | -  The value of this response header will override the value of the same response header that exists in an API response.                                                                                     |
   |                                   | -  If an API response contains multiple response headers with the same name, only the value of this response header will be returned.                                                                        |
   |                                   | -  If there is no response header with the same name in an API response, the value of this response header will be returned.                                                                                 |
   |                                   |                                                                                                                                                                                                              |
   |                                   | **Append**                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                              |
   |                                   | -  If an API response contains the specified header, the value you set here will be added, following the existing value. The two values will be separated with commas (,).                                   |
   |                                   |                                                                                                                                                                                                              |
   |                                   | -  If an API response contains multiple response headers with the same name, values of these response headers will be returned and separated with commas (,), appended by the value of this response header. |
   |                                   | -  If there is no response header with the same name in an API response, the value of this response header will be returned.                                                                                 |
   |                                   |                                                                                                                                                                                                              |
   |                                   | **Delete**                                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                              |
   |                                   | -  This response header will be deleted if a response header with the same name exists in an API response.                                                                                                   |
   |                                   | -  If an API response contains multiple response headers with the same name, all these response headers will be deleted.                                                                                     |
   |                                   |                                                                                                                                                                                                              |
   |                                   | **Skip**                                                                                                                                                                                                     |
   |                                   |                                                                                                                                                                                                              |
   |                                   | -  This response header will be skipped if a response header with the same name exists in an API response.                                                                                                   |
   |                                   | -  If an API response contains multiple response headers with the same name, values of all these response headers will be returned.                                                                          |
   |                                   | -  If there is no response header with the same name in an API response, the value of this response header will be returned.                                                                                 |
   |                                   |                                                                                                                                                                                                              |
   |                                   | **Add**                                                                                                                                                                                                      |
   |                                   |                                                                                                                                                                                                              |
   |                                   | The value of this response header will be returned in an API response even if the response contains a response header with the same name.                                                                    |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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
