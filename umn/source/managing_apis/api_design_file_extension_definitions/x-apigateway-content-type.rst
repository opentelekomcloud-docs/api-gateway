:original_name: apig_03_0124.html

.. _apig_03_0124:

x-apigateway-content-type
=========================

**Meaning**: Request content type of the API.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     /:
       get:
         x-apigateway-content-type: application/json
