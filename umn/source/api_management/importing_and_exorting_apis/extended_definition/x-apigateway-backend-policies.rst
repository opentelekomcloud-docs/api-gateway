:original_name: apig_03_0096.html

.. _apig_03_0096:

x-apigateway-backend-policies
=============================

**Meaning**: API backend policy.

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
         x-apigateway-backend-policies:
           - type: "backend endpoint type"
             name: "backend policy name"
             conditions:
               - type: "equal/enum/pattern",
                 value: "string",
                 origin: "source/request_parameter",
                 parameter_name: "string"

.. table:: **Table 1** Parameter description

   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Parameter                     | Mandatory | Type                                                           | Description                                                                                   |
   +===============================+===========+================================================================+===============================================================================================+
   | x-apigateway-backend-policies | No        | x-apigateway-backend-policies                                  | Backend policies.                                                                             |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | type                          | Yes       | String                                                         | Backend service type. The options include **HTTP**, **HTTP-VPC**, **FUNCTION**, and **MOCK**. |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | name                          | Yes       | String                                                         | Backend policy name.                                                                          |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | parameters                    | No        | :ref:`x-apigateway-backend.parameters <apig_03_0091>`          | Backend parameters.                                                                           |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | httpEndpoints                 | No        | :ref:`x-apigateway-backend.httpEndpoints <apig_03_0092>`       | HTTP service definition.                                                                      |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | httpVpcEndpoints              | No        | :ref:`x-apigateway-backend.httpVpcEndpoints <apig_03_0093>`    | HTTP-VPC service definition.                                                                  |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | functionEndpoints             | No        | :ref:`x-apigateway-backend.functionEndpoints <apig_03_0094>`   | Function service definition.                                                                  |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | mockEndpoints                 | No        | :ref:`x-apigateway-backend.mockEndpoints <apig_03_0095>`       | Mock service definition.                                                                      |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | conditions                    | Yes       | :ref:`x-apigateway-backend-policies.conditions <apig_03_0097>` | Policy condition array.                                                                       |
   +-------------------------------+-----------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
