:original_name: apig_03_0106.html

.. _apig_03_0106:

x-apigateway-is-send-fg-body-base64
===================================

**Meaning**: Whether to perform Base64 encoding on the request body used for interaction with FunctionGraph. The value is of the Boolean type.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         "x-apigateway-is-send-fg-body-base64": true

.. table:: **Table 1** Parameter description

   +-------------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
   | Parameter                           | Mandatory       | Type            | Description                                                                                          |
   +=====================================+=================+=================+======================================================================================================+
   | x-apigateway-is-send-fg-body-base64 | No              | boolean         | Specifies whether to perform Base64 encoding on the request body for interaction with FunctionGraph. |
   |                                     |                 |                 |                                                                                                      |
   |                                     |                 |                 | -  **true**: yes                                                                                     |
   |                                     |                 |                 | -  **false**: no                                                                                     |
   +-------------------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------+
