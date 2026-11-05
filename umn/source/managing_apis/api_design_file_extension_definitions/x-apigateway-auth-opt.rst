:original_name: apig_03_0115.html

.. _apig_03_0115:

x-apigateway-auth-opt
=====================

**Meaning**: App (simple authentication) parameter

**Scope of effect**: `Security Scheme Object (2.0) <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#security-scheme-object>`__/`Security Scheme Object (3.0) <https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.0.md#security-scheme-object>`__

**Swagger example:**

.. code-block::

   securityDefinitions:
     apig-auth-app:
       type: apiKey
       name: Authorization
       in: header
       x-apigateway-auth-type: AppSigv1
     apig-auth-app-header:
       type: apiKey
       name: Authorization
       in: header
       x-apigateway-auth-opt:
         appcode-auth-type: header
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       type: apiKey
       name: unused
       in: header
       x-apigateway-auth-type: IAM

**OpenAPI example**:

.. code-block::

   securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM

.. table:: **Table 1** Parameter description

   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type            | Description                                                                                |
   +===================+=================+=================+============================================================================================+
   | appcode-auth-type | No              | String          | Indicates whether AppCode authentication is enabled. The default value is **disable**.     |
   |                   |                 |                 |                                                                                            |
   |                   |                 |                 | -  **disable**: AppCode authentication is disabled.                                        |
   |                   |                 |                 | -  **header**: AppCode authentication is enabled and the AppCode is located in the header. |
   +-------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------+
