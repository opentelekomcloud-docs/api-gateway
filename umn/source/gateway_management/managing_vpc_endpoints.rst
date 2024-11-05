:original_name: apig_03_0063.html

.. _apig_03_0063:

Managing VPC Endpoints
======================

VPC endpoints are secure and private channels for connecting VPCs to VPC endpoint services.

APIs can be exposed and accessed across VPCs in the same region of the same cloud.


.. figure:: /_static/images/en-us_image_0000001278833125.jpg
   :alt: **Figure 1** Cross-VPC access in the same region

   **Figure 1** Cross-VPC access in the same region

Procedure
---------

#. Go to the APIG console.
#. In the navigation pane, choose **Gateways**.
#. Click **Access Console** or the name of the target gateway.
#. Click **VPC Endpoints** to view details. For details, see section "VPC Endpoints" in the *VPC Endpoint User Guide*.

   .. table:: **Table 1** VPC endpoint information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================+
      | VPC Endpoint Service              | Display name of the VPC endpoint service in the format "*{region}*\ **.**\ *{VPC endpoint service name}*\ **.**\ *{VPC endpoint service ID}*". You can set the VPC endpoint service name when :ref:`buying a gateway <apig_03_0037>` or later on the **VPC Endpoints** tab of the gateway. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Connections                       | VPC endpoints connected to the gateway. If you need a new VPC endpoint, click **Create VPC Endpoint**.                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **VPC Endpoint ID**: ID of a VPC endpoint.                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Packet ID**: identifier of the VPC endpoint ID.                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Status**: status of the VPC endpoint.                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   |    For details about VPC endpoint statuses, see section "What Are Statuses of VPC Endpoint Services and VPC Endpoints?" in the *VPC Endpoint User Guide*.                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Owner**: account ID. of the VPC endpoint creator. To obtain the account ID, see "Obtaining an Account Name and Account ID" in the *API Gateway API Reference*.                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Created**: time when the VPC endpoint is created.                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Operation**: whether to allow the VPC endpoint to connect to the VPC endpoint service. Accept or reject connection from the VPC endpoint to the VPC endpoint service.                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   |    .. important::                                                                                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   |       NOTICE:                                                                                                                                                                                                                                                                              |
      |                                   |       Once you reject the connection, services that run using the connection may be affected. Exercise caution.                                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Permissions                       | Specify accounts allowed to access using the VPC endpoints by adding the account IDs to the whitelist.                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | Click **Add Account** and enter an account ID. To obtain the account ID, see "Obtaining an Account Name and Account ID" in the *API Gateway API Reference*.                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Account ID**: ID of an account allowed to access using the VPC endpoints.                                                                                                                                                                                                             |
      |                                   | -  **Created**: time when the whitelist is created.                                                                                                                                                                                                                                        |
      |                                   | -  **Operation**: Manage access of the account from VPC endpoints. To forbid access of the account, remove it from the whitelist.                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
