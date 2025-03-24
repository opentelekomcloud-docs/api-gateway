:original_name: apig-api-180713011.html

.. _apig-api-180713011:

Making an API Request
=====================

This section describes the structure of a REST API request, and uses the APIG API for **creating an API group** as an example to demonstrate how to call an API.

Request URI
-----------

A request URI is in the following format:

**{URI-scheme} :// {Endpoint} / {resource-path} ? {query-string}**

Although a request URI is included in the request header, most programming languages or frameworks require the request URI to be transmitted separately.

-  **URI-scheme**: Protocol used to transmit requests. All APIs use **HTTPS**.
-  **Endpoint**: Domain name or IP address of the server bearing the REST service. It can be obtained from :ref:`Endpoints <apig-api-190529263__en-us_topic_0000001969180093_section932113578479>`. .
-  **resource-path**: Access path of an API for performing a specified operation. Obtain the path from the URI of an API. For example, the **resource-path** of the API used to create an API group is **/v2/**\ *{project_id}*\ **/apigw/instances/**\ *{instance_id}*\ **/api-groups**. *{project_id}* indicates a :ref:`project ID <apig-api-180713009>` and *{instance_id}* indicates a gateway ID. The two IDs can be obtained from the gateway information on the APIG console.
-  **query-string**: Query parameter, which is optional. Ensure that a question mark (?) is included in front of each query parameter that is in the format of *Parameter name*\ **=**\ *Parameter value*. For example, **limit=10** indicates that a maximum of 10 data records will be queried.

For example, if you want to create an API group in a region, set **URI-scheme** to **HTTPS**, **Endpoint** to **apig_endpoint**, and **resource-path** to **/v2/{project_id}/apigw/instances/{instance_id}/api-groups**. Combine the parameters in the URI.

.. code-block::

   https://{apig_endpoint}/v2/{project_id}/apigw/instances/{instance_id}/api-groups

.. note::

   To simplify the URI display in this document, each API is provided only with a **resource-path** and a request method. The **URI-scheme** of all APIs is **HTTPS**, and the endpoints of all APIs in the same region are identical.

Request Method
--------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

-  **GET**: requests the server to return specified resources.
-  **PUT**: requests the server to update specified resources.
-  **POST**: requests the server to add resources or perform special operations.
-  **DELETE**: requests the server to delete specified resources, for example, an object.
-  **HEAD**: same as GET except that the server must return only the response header.
-  **PATCH**: requests the server to update partial content of a specified resource. If the resource does not exist, a new resource will be created.

For example, in the case of the API used to create an API group, the request method is POST. The request is as follows:

.. code-block:: text

   POST https://{apig_endpoint}/v2/{project_id}/apigw/instances/{instance_id}/api-groups

Request Header
--------------

You can also add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, to request for the authentication information, add **Content-Type**, which specifies the request body type.

Common request header fields are as follows:

-  **Content-Type**: specifies the request body type or format. This field is mandatory and its default value is **application/json**. Other values of this field will be provided for specific APIs if any.
-  **X-Sdk-Date**: specifies the time when a request is sent. This field is optional. When AK/SK authentication is enabled, this field is automatically specified when SDK is used to sign the request. For more information, see :ref:`AK/SK-based Authentication <apig-api-190529268__en-us_topic_0172440411_en-us_topic_0121671869_section0390282152>`.
-  **Authorization**: specifies signature authentication information. This field is optional. When AK/SK authentication is enabled, this field is automatically specified when SDK is used to sign the request. For more information, see :ref:`AK/SK-based Authentication <apig-api-190529268__en-us_topic_0172440411_en-us_topic_0121671869_section0390282152>`.
-  **X-Auth-Token**: specifies a user token only for token-based API authentication. The user token is a response to the API used to **obtain a user token**. This API is the only one that does not require authentication.
-  **X-Project-ID**: specifies subproject ID. This field is optional and can be used in multi-project scenarios. The **X-Project-ID** field is mandatory in the request header for accessing resources in a sub-project through AK/SK-based authentication.
-  **X-Domain-ID**: specifies account ID, which is optional. When you call APIs of global services using AK/SK-based authentication, **X-Domain-ID** needs to be configured in the request header.

If AK/SK authentication is used, the requests of the API used to create an API group with the added headers are as follows:

.. code-block:: text

   POST https://{apig_endpoint}/v2/{project_id}/apigw/instances/{instance_id}/api-groups
   Content-Type: application/json
   X-Sdk-Date: 20240416T095341Z
   Authorization: SDK-HMAC-SHA256 Access=****************, SignedHeaders=content-type;host;x-sdk-date, Signature=****************

Request Body
------------

The body of a request is often sent in a structured format as specified in **Content-Type**. The request body transfers content other than the request header.

Request bodies vary between APIs. Some APIs do not require the request body, such as the APIs requested using the **GET** and **DELETE** methods.

For the API used to create an API group, you can obtain the request parameters and parameter description from the API request. Here is an example request that includes a body. The bold fields must be configured as required.

-  **name**: API group name
-  **remark**: API group description

.. code-block::

   POST https://{apig_endpoint}/v2/{project_id}/v2/{project_id}/apigw/instances/{instance_id}/api-groups
   Content-Type: application/json
   X-Sdk-Date: 20240416T095341Z
   Authorization: SDK-HMAC-SHA256 Access=****************, SignedHeaders=content-type;host;x-sdk-date, Signature=****************
   {
       "name": "APIGroup_test",
       "remark": "api group remark"
   }

If all data required for the API request is available, you can send the request to call the API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding.
