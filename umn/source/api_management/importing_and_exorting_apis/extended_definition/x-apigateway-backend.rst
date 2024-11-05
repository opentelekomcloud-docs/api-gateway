:original_name: apig_03_0090.html

.. _apig_03_0090:

x-apigateway-backend
====================

**Meaning**: API backend definition.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/users/{userId}':
       get:
         produces:
           - "application/json"
         responses:
           default:
             description: "default response"
         x-apigateway-request-type: "public"
         x-apigateway-backend:
           type: "backend endpoint type"

.. table:: **Table 1** Parameter description

   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Parameter            | Mandatory | Type                                                         | Description                                                                                   |
   +======================+===========+==============================================================+===============================================================================================+
   | x-apigateway-backend | Yes       | String                                                       | Backend service definition.                                                                   |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | type                 | Yes       | String                                                       | Backend service type. The options include **HTTP**, **HTTP-VPC**, **FUNCTION**, and **MOCK**. |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | parameters           | No        | :ref:`x-apigateway-backend.parameters <apig_03_0091>`        | Backend parameters.                                                                           |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | httpEndpoints        | No        | :ref:`x-apigateway-backend.httpEndpoints <apig_03_0092>`     | HTTP backend service definition.                                                              |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | httpVpcEndpoints     | No        | :ref:`x-apigateway-backend.httpVpcEndpoints <apig_03_0093>`  | HTTP VPC backend service definition.                                                          |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | functionEndpoints    | No        | :ref:`x-apigateway-backend.functionEndpoints <apig_03_0094>` | Function backend service definition.                                                          |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | mockEndpoints        | No        | :ref:`x-apigateway-backend.mockEndpoints <apig_03_0095>`     | Mock backend service definition.                                                              |
   +----------------------+-----------+--------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
