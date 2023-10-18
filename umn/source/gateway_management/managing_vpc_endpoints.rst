:original_name: apig-ug-0019.html

.. _apig-ug-0019:

Managing VPC Endpoints
======================

VPC endpoints are secure and private channels for connecting VPCs to VPC endpoint services.

APIs can be exposed and accessed across VPCs in the same region of the same cloud.


.. figure:: /_static/images/en-us_image_0000001197413876.jpg
   :alt: **Figure 1** Cross-VPC access in the same region

   **Figure 1** Cross-VPC access in the same region

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**.
#. Click **Access Console** next to a gateway or click the gateway name.
#. Click **VPC Endpoints** to view details. For details, see "VPC Endpoints" in the *VPC Endpoint User Guide*.

   .. table:: **Table 1** VPC endpoint information

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                |
      +===================================+============================================================================================================================================================================+
      | VPC Endpoint Service              | Name of the VPC endpoint service. When you purchase a gateway, a VPC endpoint service is automatically created and the gateway can be accessed using a VPC endpoint.       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Connections                       | VPC endpoints connected to the gateway. By default, the endpoints are connected to the VPC you selected when purchasing the gateway.                                       |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **VPC Endpoint ID**: ID of a VPC endpoint.                                                                                                                              |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **Packet ID**: identifier of the VPC endpoint ID.                                                                                                                       |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **Status**: status of the VPC endpoint.                                                                                                                                 |
      |                                   |                                                                                                                                                                            |
      |                                   |    For details about VPC endpoint statuses, see "What Are Statuses of VPC Endpoint Services and VPC Endpoints?" in the *VPC Endpoint User Guide*.                          |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **Owner**: of the VPC endpoint creator. To obtain the account ID, see "Obtaining an Account Name and Account ID" in the *API Gateway API Reference*.                    |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **Created**: time when the VPC endpoint is created.                                                                                                                     |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **Operation**: whether to allow the VPC endpoint to connect to the VPC endpoint service. Accept or reject connection from the VPC endpoint to the VPC endpoint service. |
      |                                   |                                                                                                                                                                            |
      |                                   |    .. important::                                                                                                                                                          |
      |                                   |                                                                                                                                                                            |
      |                                   |       NOTICE:                                                                                                                                                              |
      |                                   |       Once you reject the connection, services that run using the connection may be affected. Exercise caution.                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Permissions                       | Specify accounts allowed to access using the VPC endpoints by adding the account IDs to the whitelist.                                                                     |
      |                                   |                                                                                                                                                                            |
      |                                   | Click **Add Account** and enter an account ID. To obtain the account ID, see "Obtaining an Account Name and Account ID" in the *API Gateway API Reference*.                |
      |                                   |                                                                                                                                                                            |
      |                                   | -  **Account ID**: ID of an account allowed to access using the VPC endpoints.                                                                                             |
      |                                   | -  **Created**: time when the whitelist is created.                                                                                                                        |
      |                                   | -  **Operation**: Manage access of the account from VPC endpoints. To forbid access of the account, remove it from the whitelist.                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
