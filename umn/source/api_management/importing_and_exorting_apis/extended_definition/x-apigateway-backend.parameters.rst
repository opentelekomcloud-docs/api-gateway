:original_name: apig_03_0091.html

.. _apig_03_0091:

x-apigateway-backend.parameters
===============================

**Meaning**: API backend service definition.

**Scope of effect**: :ref:`x-apigateway-backend <apig_03_0090>`

**Example**:

.. code-block::

   paths:
     '/users/{userId}':
       get:
         produces:
           - "application/json"
         parameters:
           - name: "X-Auth-Token"
             description: "Authentication token"
             type: "string"
             in: "header"
             required: true
           - name: "userId"
             description: "Username"
             type: "string"
             in: "path"
             required: true
         responses:
           default:
             description: "default response"
         x-apigateway-request-type: "public"
         x-apigateway-backend:
           type: "HTTP"
           parameters:
             - name: "userId"
               value: "userId"
               in: "query"
               origin: "REQUEST"
             description: "Username"
             - name: "X-Invoke-User"
               value: "apigateway"
               in: "header"
               origin: "CONSTANT"
             description: "Caller"

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================================+
   | name            | Yes             | String          | Parameter name, which consists of a maximum of 32 bytes, starting with a letter. Only letters, digits, periods (.), hyphens (-), and underscores (_) are allowed. |
   |                 |                 |                 |                                                                                                                                                                   |
   |                 |                 |                 | The names of header parameters are not case-sensitive.                                                                                                            |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | Yes             | String          | Parameter value, which is a parameter name if the parameter comes from a request.                                                                                 |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | in              | Yes             | String          | Parameter location, which can be **header**, **query**, or **path**.                                                                                              |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | origin          | Yes             | String          | Parameter mapping source. The options include **REQUEST** and **CONSTANT**.                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | No              | String          | Parameter meaning.                                                                                                                                                |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
