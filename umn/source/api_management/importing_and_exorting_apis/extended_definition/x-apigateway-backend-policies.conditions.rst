:original_name: apig_03_0097.html

.. _apig_03_0097:

x-apigateway-backend-policies.conditions
========================================

**Meaning**: API backend policy conditions.

**Scope of effect**: :ref:`x-apigateway-backend-policies <apig_03_0096>`

**Example**:

.. code-block::

   paths:
     '/users/{userId}':
       get:
         produces:
           - "application/json"
         responses:
           default:
             description: "default response"
         x-apigateway-request-type: "public"
         x-apigateway-backend:
           type: "backend endpoint type"
         x-apigateway-backend-policies:
           - type: "backend endpoint type"
             name: "backend policy name"
             conditions:
               - type: "equal/enum/pattern",
                 value: "string",
                 origin: "source/request_parameter",
                 parameter_name: "string"

.. table:: **Table 1** Parameter description

   +-----------+-----------+--------+----------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                      |
   +===========+===========+========+==================================================================================+
   | type      | Yes       | String | Policy condition type. The options include **equal**, **enum**, and **pattern**. |
   +-----------+-----------+--------+----------------------------------------------------------------------------------+
   | value     | Yes       | String | Policy condition value.                                                          |
   +-----------+-----------+--------+----------------------------------------------------------------------------------+
   | origin    | Yes       | String | Policy condition source. The options include **source** and **request**.         |
   +-----------+-----------+--------+----------------------------------------------------------------------------------+
   | parameter | No        | String | Input parameter name if the **origin** parameter is set to **request**.          |
   +-----------+-----------+--------+----------------------------------------------------------------------------------+
