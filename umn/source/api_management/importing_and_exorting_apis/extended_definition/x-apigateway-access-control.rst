:original_name: apig_03_0102.html

.. _apig_03_0102:

x-apigateway-access-control
===========================

**Meaning**: Access control policy.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         x-apigateway-access-control: 'customAccessControlName'

.. table:: **Table 1** Parameter description

   =========================== ========= ====== ======================
   Parameter                   Mandatory Type   Description
   =========================== ========= ====== ======================
   x-apigateway-access-control No        String Access control policy.
   =========================== ========= ====== ======================
