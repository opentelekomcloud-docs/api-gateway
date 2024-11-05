:original_name: apig_03_0095.html

.. _apig_03_0095:

x-apigateway-backend.mockEndpoints
==================================

**Meaning**: Mock backend service definition.

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
           type: "MOCK"
           mockEndpoints:
             result-content: "mocked"

.. table:: **Table 1** Parameter description

   ============== ========= ====== ==============
   Parameter      Mandatory Type   Description
   ============== ========= ====== ==============
   result-content Yes       String Mock response.
   ============== ========= ====== ==============
