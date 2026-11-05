:original_name: apig_03_0121.html

.. _apig_03_0121:

x-apigateway-responses
======================

**Meaning**: Custom response.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   x-apigateway-responses:
     default:
       ACCESS_DENIED:
         status: 403
         body:
           application/json: >-
             {"error_code":"$context.error.code","error_msg":"Access
             denied","request_id":"$context.requestId"}
