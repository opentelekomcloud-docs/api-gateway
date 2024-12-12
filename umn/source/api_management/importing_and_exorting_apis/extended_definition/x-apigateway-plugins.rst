:original_name: apig_03_0105.html

.. _apig_03_0105:

x-apigateway-plugins
====================

**Meaning**: API plug-in service.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         x-apigateway-plugins: ['Plugin_mock']
   x-apigateway-plugins

.. table:: **Table 1** Parameter description

   ==================== ========= ===== ==================================
   Parameter            Mandatory Type  Description
   ==================== ========= ===== ==================================
   x-apigateway-plugins No        Array List of plug-ins bound to the API.
   ==================== ========= ===== ==================================
