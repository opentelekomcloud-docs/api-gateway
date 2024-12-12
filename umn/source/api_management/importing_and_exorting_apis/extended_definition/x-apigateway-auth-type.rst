:original_name: apig_03_0085.html

.. _apig_03_0085:

x-apigateway-auth-type
======================

**Meaning**: Swagger-based apiKey authentication format, which defines an authentication mode provided by APIG.

**Scope of effect**: `Security Scheme Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#security-scheme-object>`__/`Security Scheme Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#security-scheme-object>`__

**Swagger**:

.. code-block::

   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM

**OpenAPI example**:

.. code-block::

   securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM

.. table:: **Table 1** Parameter description

   +------------------------+-----------+--------+---------------------------------------------------------------------------+
   | Parameter              | Mandatory | Type   | Description                                                               |
   +========================+===========+========+===========================================================================+
   | x-apigateway-auth-type | Yes       | String | Authentication mode used on APIG. **AppSigv1** and **IAM** are supported. |
   +------------------------+-----------+--------+---------------------------------------------------------------------------+
   | type                   | Yes       | String | Authentication type. Only **apiKey** is supported.                        |
   +------------------------+-----------+--------+---------------------------------------------------------------------------+
   | name                   | Yes       | String | Name of the parameter for authentication.                                 |
   +------------------------+-----------+--------+---------------------------------------------------------------------------+
   | in                     | Yes       | String | Only **header** is supported.                                             |
   +------------------------+-----------+--------+---------------------------------------------------------------------------+
   | description            | No        | String | Description about the authentication.                                     |
   +------------------------+-----------+--------+---------------------------------------------------------------------------+
