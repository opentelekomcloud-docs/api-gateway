:original_name: apig_03_0089.html

.. _apig_03_0089:

x-apigateway-any-method
=======================

**Meaning**: API request method used by default if no HTTP request method is specified.

**Scope of effect**: `Path Item Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#path-item-object>`__/`Path Item Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#path-item-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         produces:
           - application/json
         responses:
           "200":
             description: "get response"
       x-apigateway-any-method:
         produces:
           - application/json
         responses:
           "200":
             description: "any response"

.. table:: **Table 1** Parameter description

   ======================= ========= ====== ===============
   Parameter               Mandatory Type   Description
   ======================= ========= ====== ===============
   x-apigateway-any-method No        String Request method.
   ======================= ========= ====== ===============
