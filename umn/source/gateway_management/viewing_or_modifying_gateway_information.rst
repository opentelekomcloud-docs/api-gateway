:original_name: apig_03_0038.html

.. _apig_03_0038:

Viewing or Modifying Gateway Information
========================================

You can view and modify the configuration of your gateways on the console.

Procedure
---------

#. Go to the APIG console.

2. In the navigation pane, choose **Gateways**.
3. Click **Access Console** or the name of the target gateway.
4. On the **Gateway Information** tab, view or modify the configuration of the gateway.

   .. table:: **Table 1** Gateway information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Modifiable Parameter              | Description                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================+
      | Basic Information                 | Basic information about the gateway, including the name, ID, edition, AZ, description, enterprise project, and maintenance time window.                                                          |
      |                                   |                                                                                                                                                                                                  |
      |                                   | -  Modify the basic information as required.                                                                                                                                                     |
      |                                   | -  To copy the gateway ID, click |image1| next to the ID.                                                                                                                                        |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Billing Mode                      | Billing mode of the gateway and the time when the gateway is created.                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Network                           | -  VPC                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                  |
      |                                   |    VPC associated with the gateway. Click the VPC name to view the configuration.                                                                                                                |
      |                                   |                                                                                                                                                                                                  |
      |                                   | -  Subnet                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                  |
      |                                   |    Subnet associated with the gateway. Click the subnet name to view the configuration.                                                                                                          |
      |                                   |                                                                                                                                                                                                  |
      |                                   | -  Security Group                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                  |
      |                                   |    Security group associated with the gateway. Click the security group name to view the configuration or click |image2| to bind a new one.                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Inbound Access                    | -  VPC Access Address                                                                                                                                                                            |
      |                                   | -  EIP                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                  |
      |                                   |    -  To bind an EIP to the gateway, click **Enable**.                                                                                                                                           |
      |                                   |    -  To copy the bound EIP, click |image3|.                                                                                                                                                     |
      |                                   |    -  Modify the bandwidth as required. The bandwidth is billed by hour based on the rate of the EIP service.                                                                                    |
      |                                   |    -  To unbind the EIP from the gateway, click **Unbind EIP**.                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Outbound Access                   | Determine whether to allow backend services of the APIs created in the gateway to be deployed on public networks. You can enable or disable outbound access at any time.                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Routes                            | Configure a private network segment that needs to communicate with the gateway. After a gateway is created, it can communicate with the VPC subnet specified during gateway creation by default. |
      |                                   |                                                                                                                                                                                                  |
      |                                   | Configure routes at your premises if the subnet of your data center is within the following three segments: 10.0.0.0/8-24, 172.16.0.0/12-24, and 192.168.0.0/16-24.                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001223730735.png
.. |image2| image:: /_static/images/en-us_image_0000001184829492.png
.. |image3| image:: /_static/images/en-us_image_0000001184669836.png
