:original_name: apig-en-ug-180621094.html

.. _apig-en-ug-180621094:

CORS
====

What Is CORS?
-------------

For security reasons, browsers restrict cross-origin requests initiated from within scripts. This means that a web application can only request resources from its origin. The CORS mechanism allows browsers to send XMLHttpRequest to servers in other domains and request access to the resources there.


.. figure:: /_static/images/en-us_image_0000001142745766.png
   :alt: **Figure 1** Process flow of the CORS mechanism

   **Figure 1** Process flow of the CORS mechanism

There are two types of CORS requests:

-  **Simple requests**

   Simple requests must meet the following conditions:

   #. The request method is HEAD, GET, or POST.
   #. The request header contains only the following fields:

      -  Accept
      -  Accept-Language
      -  Content-Language
      -  Last-Event-ID
      -  Content-Type (**application/x-www-form-urlencoded**, **multipart/form-data**, or **text/plain**)

   In the header of a simple request, browsers automatically add the **Origin** field to specify the origin (including the protocol, domain, and port) of the request. After receiving such a request, the target server determines whether the request is safe and can be accepted based on the origin. If the server sends a response containing the **Access-Control-Allow-Origin** field, the server accepts the request.

-  **Not-so-simple requests**

   Requests that do not meet the conditions for simple requests are not-so-simple requests.

   Before sending a not-so-simple request, browsers send an HTTP preflight request to the target server to confirm whether the origin the web page is loaded from is in the allowed origin list, and to confirm which HTTP request methods and header fields can be used. If the preflight request is successful, browsers send simple requests to the server.

.. _apig-en-ug-180621094__en-us_topic_0118021495_section1054782014131:

Configuring CORS
----------------

CORS is disabled by default. To enable CORS for an API, perform the operations described in this section. To customize request headers, request methods, and origins allowed for cross-domain access, create a :ref:`CORS plug-in <apig-ug-0002>`.

-  .. _apig-en-ug-180621094__en-us_topic_0118021495_li156616153578:

   **Simple CORS requests**

   When creating an API, enable CORS on the API request configuration page. For more information, see :ref:`Simple Request <apig-en-ug-180621094__en-us_topic_0118021495_section56741429495>`.

-  **Not-so-simple CORS requests**

   .. important::

      If your API will receive not-so-simple requests, **create another API that will be accessed using the OPTIONS method** in the same group as the target API to receive preflight requests.

   Follow this procedure to define the preflight request API. For more information, see :ref:`Not-So-Simple Request <apig-en-ug-180621094__en-us_topic_0118021495_section4215507492>`.

   #. On the **Set Basic Information** page, select **None** to skip over security authentication.
   #. On the **Define API Request** page, perform the following settings:

      -  **Protocol**: The same protocol used by the API with CORS enabled.
      -  **Path**: Enter a slash (/).
      -  **Method**: Select **OPTIONS**.
      -  **CORS**: Enabled.

   #. Select the **Mock** backend type.

.. _apig-en-ug-180621094__en-us_topic_0118021495_section56741429495:

Simple Request
--------------

When creating an API that will receive simple requests, :ref:`enable CORS <apig-en-ug-180621094__en-us_topic_0118021495_li156616153578>` for the API.

**Scenario 1**: If CORS is enabled and the response from the backend does not contain a CORS header, APIG handles requests from any domain, and returns the **Access-Control-Allow-Origin** header. For example:

**Request sent by a browser and containing the Origin header field:**

.. code-block:: text

   GET /simple HTTP/1.1
   Host: www.test.com
   Origin: http://www.cors.com
   Content-Type: application/x-www-form-urlencoded; charset=utf-8
   Accept: application/json
   Date: Tue, 15 Jan 2019 01:25:52 GMT

**Origin**: This field is required to specify the origin (**http://www.cors.com** in this example) of the request. APIG and the backend service determine based on the origin whether the request is safe and can be accepted.

**Response sent by the backend service:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 01:25:52 GMT
   Content-Type: application/json
   Content-Length: 16
   Server: api-gateway

   {"status":"200"}

**Response sent by APIG:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 01:25:52 GMT
   Content-Type: application/json
   Content-Length: 16
   Server: api-gateway
   X-Request-Id: 454d689fa69847610b3ca486458fb08b
   Access-Control-Allow-Origin: *

   {"status":"200"}

**Access-Control-Allow-Origin**: This field is required. The asterisk (``*``) means that APIG handles requests sent from any domain.

**Scenario 2**: If CORS is enabled and the response from the backend contains a CORS header, the header will overwrite that added by APIG. The following messages are used as examples:

**Request sent by a browser and containing the Origin header field:**

.. code-block:: text

   GET /simple HTTP/1.1
   Host: www.test.com
   Origin: http://www.cors.com
   Content-Type: application/x-www-form-urlencoded; charset=utf-8
   Accept: application/json
   Date: Tue, 15 Jan 2019 01:25:52 GMT

**Origin**: This field is required to specify the origin (**http://www.cors.com** in this example) of the request. APIG and the backend service determine based on the origin whether the request is safe and can be accepted.

**Response sent by the backend service:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 01:25:52 GMT
   Content-Type: application/json
   Content-Length: 16
   Server: api-gateway
   Access-Control-Allow-Origin: http://www.cors.com

   {"status":"200"}

**Access-Control-Allow-Origin**: Indicates that the backend service accepts requests sent from **http://www.cors.com**.

**Response sent by APIG:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 01:25:52 GMT
   Content-Type: application/json
   Content-Length: 16
   Server: api-gateway
   X-Request-Id: 454d689fa69847610b3ca486458fb08b
   Access-Control-Allow-Origin: http://www.cors.com

   {"status":"200"}

The CORS header in the backend response overwrites that in APIG's response.

.. _apig-en-ug-180621094__en-us_topic_0118021495_section4215507492:

Not-So-Simple Request
---------------------

When creating an API that will receive not-so-simple requests, enable CORS for the API by following the instructions in :ref:`Configuring CORS <apig-en-ug-180621094__en-us_topic_0118021495_section1054782014131>`, and create another API that will be accessed using the OPTIONS method.

.. note::

   If you use the CORS plug-in for an API, you do not need to create another API that uses the OPTIONS method.

The request parameters of an API accessed using the OPTIONS method must be set as follows:

-  **API Group**: The same group to which the API with CORS enabled belongs.
-  **Security Authentication**: Select **None**. No authentication is required for requests received by the new API no matter which security authentication mode has been selected.
-  **Protocol**: The same protocol used by the API with CORS enabled.
-  **Path**: Enter a slash (/) or select the path that has been set for or matches the API with CORS enabled.
-  **Method**: Select **OPTIONS**.
-  **CORS**: Enabled.

The following are example requests and responses sent to or from a mock backend.

**Request sent from a browser to an API that is accessed using the OPTIONS method:**

.. code-block::

   OPTIONS /HTTP/1.1
   User-Agent: curl/7.29.0
   Host: localhost
   Accept: */*
   Origin: http://www.cors.com
   Access-Control-Request-Method: PUT
   Access-Control-Request-Headers: X-Sdk-Date

-  **Origin**: This field is required to specify the origin from which the request has been sent.
-  **Access-Control-Request-Method**: This field is required to specify the HTTP methods to be used by the subsequent simple requests.
-  **Access-Control-Request-Headers**: This field is optional and used to specify the additional header fields in the subsequent simple requests.

**Response sent by the backend:** none

**Response sent by APIG:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 02:38:48 GMT
   Content-Type: application/json
   Content-Length: 1036
   Server: api-gateway
   X-Request-Id: c9b8926888c356d6a9581c5c10bb4d11
   Access-Control-Allow-Origin: *
   Access-Control-Allow-Headers: X-Stage,X-Sdk-Date,X-Sdk-Nonce,X-Proxy-Signed-Headers,X-Sdk-Content-Sha256,X-Forwarded-For,Authorization,Content-Type,Accept,Accept-Ranges,Cache-Control,Range
   Access-Control-Expose-Headers: X-Request-Id,X-Apig-Latency,X-Apig-Upstream-Latency,X-Apig-RateLimit-Api,X-Apig-RateLimit-User,X-Apig-RateLimit-App,X-Apig-RateLimit-Ip,X-Apig-RateLimit-Api-Allenv
   Access-Control-Allow-Methods: GET,POST,PUT,DELETE,HEAD,OPTIONS,PATCH
   Access-Control-Max-Age: 172800

-  **Access-Control-Allow-Origin**: This field is required. The asterisk (*) means that APIG handles requests sent from any domain.
-  **Access-Control-Allow-Headers**: This field is required if it is contained in the request. It indicates all header fields that can be used during cross-origin access.
-  **Access-Control-Expose-Headers**: This is the response header fields that can be viewed during cross-region access.
-  **Access-Control-Allow-Methods**: This field is required to specify which HTTP request methods the APIG supports.
-  **Access-Control-Max-Age**: This field is optional and used to specify the length of time (in seconds) during which the preflight result remains valid. No more preflight requests will be sent within the specified period.

**Request sent by a browser and containing the Origin header field:**

.. code-block:: text

   PUT /simple HTTP/1.1
   Host: www.test.com
   Origin: http://www.cors.com
   Content-Type: application/x-www-form-urlencoded; charset=utf-8
   Accept: application/json
   Date: Tue, 15 Jan 2019 01:25:52 GMT

**Response sent by the backend:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 01:25:52 GMT
   Content-Type: application/json
   Content-Length: 16
   Server: api-gateway

   {"status":"200"}

**Response sent by APIG:**

.. code-block::

   HTTP/1.1 200 OK
   Date: Tue, 15 Jan 2019 01:25:52 GMT
   Content-Type: application/json
   Content-Length: 16
   Server: api-gateway
   X-Request-Id: 454d689fa69847610b3ca486458fb08b
   Access-Control-Allow-Origin: *

   {"status":"200"}
