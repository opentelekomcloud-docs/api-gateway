:original_name: apig_03_0087.html

.. _apig_03_0087:

x-apigateway-match-mode
=======================

**Meaning**: Request URL matching mode, which can be **NORMAL** or **SWA**.

**Scope of effect**: `Operation Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#operation-object>`__/`Operation Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#operation-object>`__

**Example**:

.. code-block::

   paths:
     '/path':
       get:
         x-apigateway-match-mode: 'SWA'

.. table:: **Table 1** Parameter description

   +-------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                                                                                            |
   +=========================+=================+=================+========================================================================================================================================+
   | x-apigateway-match-mode | Yes             | String          | API matching mode. The options include **SWA** and **NORMAL**.                                                                         |
   |                         |                 |                 |                                                                                                                                        |
   |                         |                 |                 | -  **SWA**: prefix match. For example, both **/prefix/foo** and **/prefix/bar** match **/prefix**, but **/prefixpart** does not match. |
   |                         |                 |                 | -  **NORMAL**: exact match.                                                                                                            |
   +-------------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------+
