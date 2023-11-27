:original_name: apig-en-api-180713011.html

.. _apig-en-api-180713011:

Making an API Request
=====================

This section describes the structure of a REST API request, and uses the APIG API for creating an API group (dedicated gateways) as an example to demonstrate how to call an API.

Request URI
-----------

A request URI is in the following format:

**{URI-scheme} :// {Endpoint} / {resource-path} ? {query-string}**

Although a request URI is included in the request header, most programming languages or frameworks require the request URI to be transmitted separately.

.. table:: **Table 1** URI parameters

   +---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
   +===============+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | URI-scheme    | Protocol used to transmit requests. All APIs use HTTPS.                                                                                                                                                                                                                                                                                                                                                                                                                                |
   +---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint      | Domain name or IP address of the server bearing the REST service. The endpoint varies between services in different regions. It can be obtained from :ref:`Endpoints <apig-api-190529265>`.                                                                                                                                                                                                                                                                                            |
   +---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path | Access path of an API for performing a specified operation. Obtain the path from the URI of an API. For example, the **resource-path** of the API used to create an API group in a dedicated gateway is **/v2/**\ *{project_id}*\ **/apigw/instances/**\ *{instance_id}*\ **/api-groups**. *{project_id}* indicates a :ref:`project ID <apig-api-180713009>` and *{instance_id}* indicates a gateway ID. The two IDs can be obtained from the gateway information on the APIG console. |
   +---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string  | Query parameter, which is optional. Ensure that a question mark (?) is included before each query parameter that is in the format of "*Parameter name*\ =\ *Parameter value*". For example, **?limit=10** indicates that a maximum of 10 data records will be displayed. Separate multiple query parameters with ampersands (&).                                                                                                                                                       |
   +---------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

For example, to create an API group in a region, combine the parameters in the URI. *apig_endpoint* indicates the endpoint of APIG.

.. code-block::

   https://{apig_endpoint}/v2/{project_id}/apigw/instances/{instance_id}/api-groups

.. note::

   To simplify the URI display in this document, each API is provided only with a **resource-path** and a request method. The **URI-scheme** of all APIs is **HTTPS**, and the endpoints of all APIs in the same region are identical.

Request Methods
---------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

-  **GET**: requests the server to return specified resources.
-  **PUT**: requests the server to update specified resources.
-  **POST**: requests the server to add resources or perform special operations.
-  **DELETE**: requests the server to delete specified resources, for example, an object.
-  **HEAD**: same as GET except that the server must return only the response header.
-  **PATCH**: requests the server to update partial content of a specified resource. If the resource does not exist, a new resource will be created.

For example, in the case of the API used to create an API group (dedicated gateways), the request method is POST. The request is as follows:

.. code-block:: text

   POST https://{apig_endpoint}/v2/{project_id}/apigw/instances/{instance_id}/api-groups

Request Header
--------------

You can also add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, to request for the authentication information, add **Content-Type**, which specifies the request body type.

Common request header fields are as follows:

-  **Content-Type**: specifies the request body type or format. This field is mandatory and its default value is **application/json**. Other values of this field will be provided for specific APIs if any.

-  **X-Auth-Token**: specifies a user token only for token-based API authentication. The user token is a response to the API used to obtain a user token.

   .. note::

      In addition to supporting token-based authentication, APIs also support authentication using access key ID/secret access key (AK/SK). During AK/SK-based authentication, an SDK is used to sign the request, and the **Authorization** (signature information) and **X-Sdk-Date** (time when the request is sent) header fields are automatically added to the request.

      For more information, see :ref:`AK/SK-based Authentication <apig-api-190529268__en-us_topic_0121671869_section0390282152>`.

   The API used to obtain a user token does not require authentication. Therefore, only the **Content-Type** field needs to be added to requests for calling the API. An example of such requests is as follows:

   .. code-block:: text

      POST https://{iam_endpoint}/v3/auth/tokens
      Content-Type: application/json

Request Body
------------

The body of a request is often sent in a structured format as specified in the **Content-Type** header field. The request body transfers content except the request header.

The request body varies between APIs. Some APIs do not require the request body, such as the APIs requested using the GET and DELETE methods.

In the case of the API used to create an API group (dedicated gateways), the request parameters and parameter description can be obtained from the API request. The following provides an example request with a body included. Replace *name* (API group name) and *remark* (API group description) with the actual values.

.. code-block:: text

   POST https://{apig_endpoint}/v2/{project_id}/v2/{project_id}/apigw/instances/{instance_id}/api-groups
   Content-Type: application/json
   X-Auth-Token: xxxx
   {
       "name": "APIGroup_test",
       "remark": "api group remark"
   }

If all data required for the API request is available, you can send the request to call the API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding.
