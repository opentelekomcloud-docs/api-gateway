:original_name: apig_03_0120.html

.. _apig_03_0120:

x-apigateway-response
=====================

**Meaning**: API response name.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     /:
       get:
         x-apigateway-response: test
