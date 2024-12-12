:original_name: apig_03_0098.html

.. _apig_03_0098:

x-apigateway-ratelimit
======================

**Meaning**: Request throttling policy.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         x-apigateway-ratelimit: 'customRatelimitName'

.. table:: **Table 1** Parameter description

   ====================== ========= ====== ==========================
   Parameter              Mandatory Type   Description
   ====================== ========= ====== ==========================
   x-apigateway-ratelimit No        String Request throttling policy.
   ====================== ========= ====== ==========================
