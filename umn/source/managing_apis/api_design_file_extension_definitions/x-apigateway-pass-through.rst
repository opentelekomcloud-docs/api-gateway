:original_name: apig_03_0122.html

.. _apig_03_0122:

x-apigateway-pass-through
=========================

**Meaning**: Indicates whether to pass through API request parameters. **always**: yes; **never**: no.

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
             x-apigateway-sample: ''
             name: test
             in: query
             required: true
