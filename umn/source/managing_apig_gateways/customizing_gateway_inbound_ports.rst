:original_name: apig_03_0109.html

.. _apig_03_0109:

Customizing Gateway Inbound Ports
=================================

If different service teams need to provide their own APIs through the same API gateway and require port-level isolation, you can customize inbound ports. APIG supports inbound port customization for gateways so that clients can access different backend services through different ports.

Constraints
-----------

-  Only one protocol can be configured for a port. Only HTTP and HTTPS are supported.
-  For details about the constraints on independent domain names and ports, see :ref:`Constraints <apig_03_0006__section53771439658>`.


Customizing Gateway Inbound Ports
---------------------------------

#. Go to the APIG console.

#. In the navigation pane, choose **Gateways**.

#. Click **Access Console** or the name of the target gateway.

#. On the **Inbound Port** tab page, click **Add Inbound Port**.

   Select a request protocol and enter the inbound port number based on the actual service requirements.

   .. table:: **Table 1** Inbound port configuration

      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Description                                                                                                                                                                                               |
      +==================+===========================================================================================================================================================================================================+
      | Request Protocol | Request protocol for accessing a gateway. Both HTTP and HTTPS are supported. Select HTTPS for services that require high data transmission security. HTTPS must be used together with an SSL certificate. |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Inbound Port     | Port number for accessing a gateway. Range: 1024 to 49151.                                                                                                                                                |
      +------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   In the port list, if the new inbound port and its status are displayed as normal, the port is successfully created.

Related Documents
-----------------

-  In the :ref:`Independent Domain Names <apig_03_0006>` area on the **Group Information** tab, change the port bound to an independent domain name to the new inbound port or select the new inbound port when binding an independent domain name. In this way, you can access different backend services through different ports.
