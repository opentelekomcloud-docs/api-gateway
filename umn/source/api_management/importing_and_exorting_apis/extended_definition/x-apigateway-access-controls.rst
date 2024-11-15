:original_name: apig_03_0103.html

.. _apig_03_0103:

x-apigateway-access-controls
============================

**Meaning**: Mapping between an access control policy name and limit settings.

**Scope of effect**: `Swagger Object <https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#swagger-object>`__

**Example**:

.. code-block::

   x-apigateway-access-controls:
     customAccessControlName:
       acl-type: "DENY"
       entity-type: "IP"
       value: 127.0.0.1,192.168.0.1/16

.. table:: **Table 1** Parameter description

   +-------------------------+-----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type                                                      | Description                                                                                  |
   +=========================+=================+===========================================================+==============================================================================================+
   | customAccessControlName | No              | :ref:`x-apigateway-access-controls.policy <apig_03_0104>` | Name of an access control policy.                                                            |
   |                         |                 |                                                           |                                                                                              |
   |                         |                 |                                                           | To use the policy, set :ref:`x-apigateway-access-control <apig_03_0102>` to the policy name. |
   +-------------------------+-----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------+
