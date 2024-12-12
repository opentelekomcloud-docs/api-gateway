:original_name: apig_03_0093.html

.. _apig_03_0093:

x-apigateway-backend.httpVpcEndpoints
=====================================

**Meaning**: HTTP VPC backend service definition.

**Scope of effect**: :ref:`x-apigateway-backend <apig_03_0090>`

**Example**:

.. code-block::

   paths:
     '/users/{userId}':
       get:
         produces:
           - "application/json"
         parameters:
           - name: "X-Auth-Token"
             description: "Authentication token"
             type: "string"
             in: "header"
             required: true
         responses:
           default:
             description: "default response"
         x-apigateway-request-type: "public"
         x-apigateway-backend:
           type: "HTTP-VPC"
           httpVpcEndpoints:
             name: "vpc-test-1"
             scheme: "http"
             method: "GET"
             path: "/users"
             timeout: 30000

.. table:: **Table 1** Parameter description

   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                                                                        |
   +===========+===========+========+====================================================================================================================================+
   | name      | Yes       | Array  | VPC channel name.                                                                                                                  |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | scheme    | Yes       | String | Backend request protocol. HTTP and HTTPS are supported.                                                                            |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | method    | Yes       | String | Backend request method. The options include **GET**, **POST**, **PUT**, **DELETE**, **HEAD**, **OPTIONS**, **PATCH**, and **ANY**. |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | path      | Yes       | String | Backend request path, which can contain variables.                                                                                 |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | timeout   | No        | Number | Backend request timeout in milliseconds. The range is 1-60,000, and the default value is **5000**.                                 |
   +-----------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
