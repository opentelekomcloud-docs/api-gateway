:original_name: apig_03_0117.html

.. _apig_03_0117:

x-apigateway-result-normal-sample
=================================

**Meaning**: Example of a successful response.

**Scope of effect**: `Operation Responses <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#responsesObject>`__

**Example**:

.. code-block::

   paths:
     /:
       get:
         responses:
           default:
             x-apigateway-result-normal-sample: success
