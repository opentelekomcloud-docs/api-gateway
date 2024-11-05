:original_name: apig_03_0099.html

.. _apig_03_0099:

x-apigateway-ratelimits
=======================

**Meaning**: Mapping between a request throttling policy name and limit values.

**Scope of effect**: `Swagger Object <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#swagger-object>`__

**Example**:

.. code-block::

   x-apigateway-ratelimits:
     customRatelimitName:
       api-limit: 200
       app-limit: 200
       user-limit: 200
       ip-limit: 200
       interval: 1
       unit: second/minute/hour
       shared: true
       special:
         - type: APP
           limit: 100
           instance: xxxxxxxxx

.. table:: **Table 1** Parameter description

   +---------------------+-----------------+------------------------------------------------------+-----------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type                                                 | Description                                                                             |
   +=====================+=================+======================================================+=========================================================================================+
   | customRatelimitName | No              | :ref:`x-apigateway-ratelimits.policy <apig_03_0100>` | Name of a request throttling policy.                                                    |
   |                     |                 |                                                      |                                                                                         |
   |                     |                 |                                                      | To use the policy, set :ref:`x-apigateway-ratelimit <apig_03_0098>` to the policy name. |
   +---------------------+-----------------+------------------------------------------------------+-----------------------------------------------------------------------------------------+
