:original_name: apig-api-180713206.html

.. _apig-api-180713206:

HTTP Status Codes
=================

:ref:`Table 1 <apig-api-180713206__en-us_topic_0172449737_table11812530035>` describes common status codes.

.. _apig-api-180713206__en-us_topic_0172449737_table11812530035:

.. table:: **Table 1** HTTP status codes

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Status Code & Message             | Description                                                                                                                                             |
   +===================================+=========================================================================================================================================================+
   | 200 OK                            | The request has been processed successfully.                                                                                                            |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 204 No Content                    | The server successfully processed the request and is not returning any content.                                                                         |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 400 Bad Request                   | The server failed to process the request. Possible causes include:                                                                                      |
   |                                   |                                                                                                                                                         |
   |                                   | #. Malformed request syntax                                                                                                                             |
   |                                   | #. Invalid request message framing                                                                                                                      |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | The request requires user authentication. For example, the username and password are required.                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | The server understood the request, but is refusing to fulfill it.                                                                                       |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The server has not found anything matching the request URI.                                                                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | The method specified in the request line is not allowed for the resource identified by the request URI.                                                 |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server could not be accepted by the client.                                                                               |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must first authenticate yourself with the proxy.                                                                                                    |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The server timed out waiting for the request.                                                                                                           |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request could not be completed due to a conflict with the current state of the resource.                                                            |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 410 Gone                          | The requested resource is no longer available at the server and no forwarding address is known.                                                         |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 412 Precondition Failed           | The server does not meet one of the preconditions that the requester put on the request.                                                                |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | The server encountered an unexpected condition which prevented it from fulfilling the request.                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | The server does not support the functionality required to fulfill the request.                                                                          |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | The server, while acting as a gateway or proxy, received an invalid response from the upstream server it accessed in attempting to fulfill the request. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | The request could not be processed by the server because the server is being maintained or overloaded.                                                  |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | The server was acting as a gateway or proxy and did not receive a timely response from the upstream server.                                             |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
