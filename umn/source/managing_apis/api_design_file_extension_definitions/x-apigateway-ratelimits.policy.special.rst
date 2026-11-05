:original_name: apig_03_0101.html

.. _apig_03_0101:

x-apigateway-ratelimits.policy.special
======================================

**Meaning**: Definition of a special request throttling policy.

**Scope of effect**: :ref:`x-apigateway-ratelimits.policy <apig_03_0100>`

**Example**:

.. code-block::

   x-apigateway-ratelimits:
     customRatelimitName:
       api-limit: 200
       app-limit: 200
       user-limit: 200
       ip-limit: 200
       interval: 1
       unit: MINUTE
       shared: false
       special:
         - type: USER
           limit: 100
           instance: xxxxxxxx

.. table:: **Table 1** Parameter description

   +-----------+-----------+--------+---------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                               |
   +===========+===========+========+===========================================================================+
   | type      | Yes       | String | Special request throttling policy type, which can be **APP** or **USER**. |
   +-----------+-----------+--------+---------------------------------------------------------------------------+
   | limit     | Yes       | Number | Access limit.                                                             |
   +-----------+-----------+--------+---------------------------------------------------------------------------+
   | instance  | Yes       | String | ID of an excluded app or user.                                            |
   +-----------+-----------+--------+---------------------------------------------------------------------------+
