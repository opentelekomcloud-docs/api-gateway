:original_name: apig_03_0078.html

.. _apig_03_0078:

Creating a gRPC API
===================

APIG supports gRPC API creation. gRPC is a modern, open-source, high-performance Remote Procedure Call (RPC) framework that can run in any environment. You only need to define the request and response of each API, and let the gRPC framework take care of the rest. gRPC uses protocol buffers (protobuf) as its Interface Definition Language (IDL) and for bottom-layer message exchange. The following table compares gRPC and REST APIs.

.. table:: **Table 1** gRPC vs REST

   +--------------------------+-----------------------------------------------------------+------------------------------------------------------+
   | Parameter                | gRPC                                                      | REST                                                 |
   +==========================+===========================================================+======================================================+
   | Message encoding         | protobuf                                                  | JSON                                                 |
   +--------------------------+-----------------------------------------------------------+------------------------------------------------------+
   | Transmission protocol    | HTTP/2                                                    | HTTP                                                 |
   +--------------------------+-----------------------------------------------------------+------------------------------------------------------+
   | Transmission performance | Fast, with less content to transmit                       | More content to transmit                             |
   +--------------------------+-----------------------------------------------------------+------------------------------------------------------+
   | Transmission mode        | -  Unary RPC                                              | Send a single request and receive a single response. |
   |                          |                                                           |                                                      |
   |                          |    Send a single request and receive a single response.   |                                                      |
   |                          |                                                           |                                                      |
   |                          | -  Server streaming RPC                                   |                                                      |
   |                          |                                                           |                                                      |
   |                          |    Send a single request and receive multiple responses.  |                                                      |
   |                          |                                                           |                                                      |
   |                          | -  Client streaming RPC                                   |                                                      |
   |                          |                                                           |                                                      |
   |                          |    Send multiple requests and receive a single response.  |                                                      |
   |                          |                                                           |                                                      |
   |                          | -  Bidirectional streaming RPC                            |                                                      |
   |                          |                                                           |                                                      |
   |                          |    Send multiple requests and receive multiple responses. |                                                      |
   +--------------------------+-----------------------------------------------------------+------------------------------------------------------+

If both your client and server are of the gRPC type, you can create an gRPC API to open up your backend capabilities. gRPC features low resource consumption and high transmission rate. It is suitable for internal service invocation and governance.

Restrictions
------------

-  gRPC APIs cannot be imported, exported, or debugged, and do not support the import of API design files, CSE microservices, or CCE workloads.
-  Circuit breaker policies whose backend policy type is **Mock**, **HTTP&HTTPS**, or **FunctionGraph** are not supported.

Prerequisites
-------------

-  You have created an API group. If no API group is available, create one by referring to :ref:`Creating an API Group <apig_03_0005>`.

-  If the backend service needs to use a load balance channel, :ref:`create a channel <apig_03_0040>` first.

-  .. _apig_03_0078__en-us_topic_0000001665148893_li119739165810:

   The backend service has a proto file that defines API request and response parameters. The proto file is used in gRPC to define data structures and service APIs. It describes data structures and interactions using protobuf and serves as a contract for communication between the client and backend services.

Procedure
---------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3.  In the navigation pane, choose **API Management** > **API Groups**.

4.  Click a group name.

5.  On the **APIs** tab page, choose **Create API** > **Create gRPC API**.

6.  Configure the frontend definition according to :ref:`5.a <apig_03_0010__en-us_topic_0000001176135914_li1051155861918>`.

    For gRPC APIs, the default frontend request method is **POST** and the protocol is **GRPCS**.

    Set the path to any of the following:

    -  /
    -  /*{Package name}*.\ *{Service name}*
    -  /*{Package name}*.\ *{Service name}*/*{Method name}*

    .. note::

       -  Obtain the package name, service name, and method name from the :ref:`proto file <apig_03_0078__en-us_topic_0000001665148893_li119739165810>`.
       -  Absolute match can be used only when the frontend path is set to **/**\ *{Package name}*\ **.**\ *{Service name}*\ **/**\ *{Method name}*.
       -  Base64 encoding is not supported.

7.  Configure the authentication mode by referring to :ref:`5.b <apig_03_0010__en-us_topic_0000001176135914_li6358122832510>`.

8.  Click **Next**.

9.  Configure the default backend by referring to :ref:`1 <apig_03_0010__en-us_topic_0000001176135914_en-us_topic_0000001126143529_li12956182663810>`.

    The backend service type of gRPC APIs can be **GRPC&GRPCS** or **FunctionGraph**.

    -  When the type is **GRPC&GRPCS**, the backend service uses the **POST** request method, **/** path, and **GRPC** or **GRPCS** protocol, and does not support parameter orchestration.
    -  When the type is FunctionGraph, the backend service uses **V2** network architecture and **Synchronous** invocation type by default, and does not support parameter orchestration.

10. (Optional) Add a backend policy by referring to :ref:`5 <apig_03_0010__en-us_topic_0000001176135914_en-us_topic_0000001126143529_li16876454181218>`.

(Optional) Creating a Policy
----------------------------

You can create policies for the API after publishing it.

#. On the **APIs** tab, click **Create Policy**.
#. Select a policy type and set parameters.

   -  Select existing policy
   -  Create new policy (see :ref:`Creating a Policy and Binding It to APIs <apig_03_0019>`)

#. Click **OK**.
