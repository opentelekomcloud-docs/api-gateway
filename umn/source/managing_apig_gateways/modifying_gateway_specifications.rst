:original_name: apig_03_0064.html

.. _apig_03_0064:

Modifying Gateway Specifications
================================

If the specifications of a gateway cannot meet your service requirements, upgrade the specifications.

Billing
-------

-  For pay-per-use gateways, pay for what you use without needing to pay for any extra fees.

Constraints
-----------

-  During the specification change, the persistent connection is intermittently disconnected and needs to be re-established. You are advised to change the specifications during off-peak hours.
-  Specifications can be upgraded but cannot be downgraded.
-  Changing the gateway edition will also change the private network access IP addresses. Remove your firewall or whitelist configuration to prevent services from being affected by network issues. Do not perform any operations on the gateway during the change. After the change is complete, adjust the firewall or whitelist configuration based on service requirements.
-  If the current gateway does not support specification changing, contact technical support to upgrade the gateway to the latest version.
-  During the specification change, metrics may be slightly different.


Modifying Gateway Specifications
--------------------------------

#. Go to the APIG console.
#. In the navigation pane, choose **Gateways**.

3. Choose **More** > **Modify Specifications** on the right of the target gateway.
4. Select an edition and click **Next**. For details about the gateway parameters, see :ref:`Table 1 <apig_03_0038__table14750184110266>`.
5. Confirm the configuration, read and confirm your acceptance of the service agreement, and click **Pay Now**. The upgrade takes 15 to 30 minutes to complete.
