:original_name: apic-ug-190430106.html

.. _apic-ug-190430106:

Deleting a Custom Authorizer
============================

Scenario
--------

You can delete custom authorizers you no longer require.

.. note::

   -  Custom authentication is implemented using FunctionGraph and not supported if FunctionGraph is unavailable in the selected region.
   -  Custom authorizers that have been configured for APIs cannot be deleted.

Prerequisites
-------------

You have :ref:`created a custom authorizer <apic-ug-190430105>`.

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. Choose **API Publishing** > **Custom Authorizers**, and click **Delete** in the row containing the custom authorizer you want to delete.
#. Click **Yes**.
