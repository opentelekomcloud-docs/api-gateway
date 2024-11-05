:original_name: apig_03_0086.html

.. _apig_03_0086:

x-apigateway-request-type
=========================

**Meaning**: API request type, which can be **public** or **private**.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         x-apigateway-request-type: 'public'

.. table:: **Table 1** Parameter description

   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------+
   | Parameter                 | Mandatory       | Type            | Description                                                     |
   +===========================+=================+=================+=================================================================+
   | x-apigateway-request-type | Yes             | String          | API visibility. The options include **public** and **private**. |
   |                           |                 |                 |                                                                 |
   |                           |                 |                 | -  **public**: The API can be made available for sale.          |
   |                           |                 |                 | -  **private**: The API will not be available for sale.         |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------+
