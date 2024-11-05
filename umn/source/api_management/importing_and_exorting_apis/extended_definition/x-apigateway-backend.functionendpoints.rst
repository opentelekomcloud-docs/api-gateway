:original_name: apig_03_0094.html

.. _apig_03_0094:

x-apigateway-backend.functionEndpoints
======================================

**Meaning**: Function backend service definition.

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
         responses:
           default:
             description: "default response"
         x-apigateway-request-type: "public"
         x-apigateway-backend:
           type: "FUNCTION"
           functionEndpoints:
             version: "v1"
             function-urn: ""
             invocation-type: "synchronous"
             timeout: 30000

.. table:: **Table 1** Parameter description

   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory | Type   | Description                                                                                 |
   +=================+===========+========+=============================================================================================+
   | function-urn    | Yes       | String | Function URN.                                                                               |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | version         | Yes       | String | Function version.                                                                           |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | invocation-type | Yes       | String | Function invocation type. The value can be **async** or **sync**.                           |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | timeout         | No        | Number | Function timeout in milliseconds. The range is 1-60,000, and the default value is **5000**. |
   +-----------------+-----------+--------+---------------------------------------------------------------------------------------------+
