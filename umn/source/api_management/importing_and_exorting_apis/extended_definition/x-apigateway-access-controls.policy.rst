:original_name: apig_03_0104.html

.. _apig_03_0104:

x-apigateway-access-controls.policy
===================================

**Meaning**: Definition of an access control policy.

**Scope of effect**: :ref:`x-apigateway-access-controls <apig_03_0103>`

**Example**:

.. code-block::

   x-apigateway-access-controls:
     customAccessControlName:
       acl-type: "DENY"
       entity-type: "IP"
       value: 127.0.0.1,192.168.0.1/16

.. table:: **Table 1** Parameter description

   +-------------+-----------+--------+---------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                         |
   +=============+===========+========+=====================================================================+
   | acl-type    | Yes       | String | Access control effect. The options include **PERMIT** and **DENY**. |
   +-------------+-----------+--------+---------------------------------------------------------------------+
   | entity-type | Yes       | String | Access control object. Only IP addresses are supported.             |
   +-------------+-----------+--------+---------------------------------------------------------------------+
   | value       | Yes       | String | Access control values, which are separated with commas (,).         |
   +-------------+-----------+--------+---------------------------------------------------------------------+
