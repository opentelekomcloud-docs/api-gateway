:original_name: apig_03_0088.html

.. _apig_03_0088:

x-apigateway-cors
=================

**Meaning**: Specifies whether CORS is supported. The value is of the Boolean type.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         x-apigateway-cors: true

.. table:: **Table 1** Parameter description

   +-------------------+-----------------+-----------------+---------------------------+
   | Parameter         | Mandatory       | Type            | Description               |
   +===================+=================+=================+===========================+
   | x-apigateway-cors | Yes             | boolean         | Whether to support CORS.  |
   |                   |                 |                 |                           |
   |                   |                 |                 | -  **true**: support      |
   |                   |                 |                 | -  **false**: not support |
   +-------------------+-----------------+-----------------+---------------------------+

For the API request for enabling CORS, the headers listed in the following table will be added to the response.

+------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Header                       | Value                                                                                                                                                                | Description                                                     |
+==============================+======================================================================================================================================================================+=================================================================+
| Access-Control-Max-Age       | 172800                                                                                                                                                               | Maximum time the response of a preflight request can be cached. |
|                              |                                                                                                                                                                      |                                                                 |
|                              |                                                                                                                                                                      | Unit: s                                                         |
+------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Access-Control-Allow-Origin  | \*                                                                                                                                                                   | Requests from any domain are allowed.                           |
+------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Access-Control-Allow-Headers | X-Sdk-Date, X-Sdk-Nonce, X-Proxy-Signed-Headers, X-Sdk-Content-Sha256, X-Forwarded-For, Authorization, Content-Type, Accept, Accept-Ranges, Cache-Control, and Range | Headers that can be used by a formal request.                   |
+------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
| Access-Control-Allow-Methods | GET, POST, PUT, DELETE, HEAD, OPTIONS, and PATCH                                                                                                                     | Methods that can be used by a formal request.                   |
+------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------+
