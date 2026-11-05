:original_name: apig_01_0012.html

.. _apig_01_0012:

Product Functions
=================

This section outlines the key features supported by APIG. For detailed information on regional availability of each feature, you can refer to the console.

API Lifecycle Management
------------------------

The lifecycle of an API involves creating, publishing, removing, and deleting the API. API lifecycle management enables you to quickly and efficiently expose service capabilities. For details, see :ref:`Process Flow <apig_03_0127>`.

Convenient Debugging Tool
-------------------------

With the built-in debugging tool, you can debug APIs using different HTTP headers and request bodies. This tool simplifies the API development process and reduces the API development and maintenance costs. For details, see :ref:`Debugging an API <apig_03_0012>`.

Version Management
------------------

An API can be published in different environments. Publishing an API again in the same environment will override the API's previous version. APIG displays the publication history (including the version, description, date and time, and environment) of each API. You can roll back an API to any historical version to meet dark launch and version upgrade requirements. For details, see :ref:`Publishing an API <apig_03_0014>`.

Environment Variables
---------------------

Environment variables are manageable and specific to environments. Variables of an API will be replaced by the values of the variables in the environment where the API will be published. You can create variables in different environments to call different backend services using the same API. For details, see :ref:`(Optional) Configuring the Environment and Environment Variables <apig_03_0007>`.

Refined Request Throttling
--------------------------

-  For different service demands and user levels, you can control the frequency at which an API can be called by a user, credential, or IP address, ensuring that backend services can run stably. For details, see :ref:`Configuring API Request Throttling <apig_03_0025>`.
-  Configure different request throttling limits with API path, query, and header parameters. For details, see :ref:`Configuring API Request Throttling <apig_03_0025>`.
-  The throttling can be accurate to the second, minute, hour, or day.
-  Set throttling limits for excluded credentials and tenants.

Monitoring and Alarm
--------------------

APIG provides visualized, real-time API monitoring, and displays multiple metrics, including number of requests, invocation latency, data traffic, and number of errors. The metrics help you understand the API usage, allowing you to identify potential service risks. For details, see :ref:`Configuring an Alarm Rule <apig_03_0033>`.

Security Protection
-------------------

-  Domain name access can be authenticated with TLS 1.1 and TLS 1.2. mTLS two-way authentication is supported. For details, see :ref:`Configuring the Domain Name for Calling APIs <apig_03_0006>`.
-  Access control policies limit API access from specific IP addresses or accounts. You can blacklist or whitelist certain IP addresses and accounts to access your APIs. For details, see :ref:`Configuring API Access Control <apig_03_0027>`.
-  Circuit breaker policies protect your backend services through degradation if they are abnormal. For details, see :ref:`Circuit Breaker <apig_03_0023>`.
-  Identity authentication includes frontend authentication and backend authentication. Frontend authentication supports IAM authentication using AK/SK and token, and allows users to customize API access authentication logic using functions and signature keys for backend services to verify the identity of API gateways. Backend authentication supports TLS two-way authentication and allows users to customize API access authentication logic using functions.

Load Balance Channel
--------------------

Virtual Private Cloud (VPC) channels (load balance channels) can be created for accessing resources in VPCs and exposing backend services deployed in VPCs. VPC channels balance API requests to backend services. For details, see :ref:`(Optional) Creating a Load Balance Channel <apig_03_0040>`.

Mock Responses
--------------

Mock backends simulate API responses for circuit breakers, service degradation, and redirection.

.. _apig_01_0012__section2644533103712:

HTTP 2.0
--------

APIG supports HTTP/2, which is a major revision of HTTP and was originally named HTTP 2.0. It features capabilities such as binary framing, multiplexing, and header compression, improving transmission performance to achieve low latency and high throughput.

-  Binary encoding

   Unlike HTTP 1.x where data is transmitted in text format, data in HTTP 2.0 is split into messages and frames for binary encoding. Compared with string (text) parsing, binary parsing is easier and less error-prone and delivers higher transmission performance.

-  Multiplexing

   With binary encoding, HTTP 2.0 no longer relies on multiple connections to process and send requests and responses concurrently.

   For the same domain name, all requests are completed on a single connection, and each connection can process any number of messages. A message consists of one or more frames, which can be sent out of order and finally recombined based on the stream ID in the header of each frame. This shortens the latency and improves the efficiency.

-  Header compression

   HTTP 2.0 uses an encoder to reduce the size of the headers to transmit. Both the client and server store a header field table to avoid transmitting same headers repeatedly, achieving high throughput.

.. note::

   -  HTTP 2.0 strongly depends on network stability. To use HTTP 2.0, ensure that your network is stable and your client supports this protocol.
   -  If your gateway does not support HTTP 2.0, contact technical support to upgrade it.
   -  To disable HTTP 2.0, turn off **HTTP/2** under the **request_custom_config** parameter on the **Parameters** tab page of the APIG console.
