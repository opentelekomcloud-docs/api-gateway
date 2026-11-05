:original_name: apig_03_0118.html

.. _apig_03_0118:

x-apigateway-result-failure-sample
==================================

**Meaning**: Example of a failed response.

**Scope of effect**: `Operation Responses <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#responsesObject>`__

**Example**:

.. code-block::

   paths:
     /:
       get:
         responses:
           default:
             x-apigateway-result-failure-sample: fail
