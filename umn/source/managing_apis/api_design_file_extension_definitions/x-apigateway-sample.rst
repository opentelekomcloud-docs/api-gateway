:original_name: apig_03_0123.html

.. _apig_03_0123:

x-apigateway-sample
===================

**Meaning**: Example values of API request parameters.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     /:
       get:
         parameters:
           - maximum: 0
             minimum: 0
             maxLength: 0
             minLength: 0
             type: string
             x-apigateway-orchestrations: []
             x-apigateway-pass-through: always
             x-apigateway-sample: 'test-sample'
             name: test
             in: query
             required: true
