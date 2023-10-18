:original_name: apig-en-ug-180425084.html

.. _apig-en-ug-180425084:

Editing Health Check Configurations
===================================

Scenario
--------

You can modify the health check configurations of a VPC channel to meet service requirements.

Prerequisites
-------------

You have created a VPC channel.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **VPC Channels**.

#. Click the name of the target VPC channel,

#. Click the **Health Check** tab.

#. Click **Edit Health Check**.

#. In the **Edit Health Check Configuration** dialog box, modify the parameters listed in :ref:`Table 1 <apig-en-ug-180425084__table4566428105819>`.

   .. _apig-en-ug-180425084__table4566428105819:

   .. table:: **Table 1** Health check configurations

      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                           |
      +===================================+=======================================================================================================+
      | Protocol                          | The protocol used to perform health checks on cloud servers associated with the VPC channel. Options: |
      |                                   |                                                                                                       |
      |                                   | -  TCP                                                                                                |
      |                                   | -  HTTP                                                                                               |
      |                                   | -  HTTPS                                                                                              |
      |                                   |                                                                                                       |
      |                                   | Default value: **TCP**.                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Path                              | The destination path for health checks.                                                               |
      |                                   |                                                                                                       |
      |                                   | Set this parameter only when **Protocol** is not set to **TCP**.                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Check Port                        | The destination port for health checks.                                                               |
      |                                   |                                                                                                       |
      |                                   | By default, the port of the VPC channel will be used.                                                 |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Healthy Threshold                 | The number of consecutive successful checks required for a cloud server to be considered healthy.     |
      |                                   |                                                                                                       |
      |                                   | Range: 2-10. Default value: **2**.                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Unhealthy Threshold               | The number of consecutive failed checks required for a cloud server to be considered unhealthy.       |
      |                                   |                                                                                                       |
      |                                   | Range: 2-10. Default value: **5**.                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Timeout (s)                       | The timeout used to determine whether a health check has failed. Unit: s.                             |
      |                                   |                                                                                                       |
      |                                   | Range: 2-30. Default value: **5**.                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Interval (s)                      | The interval between consecutive checks. Unit: s.                                                     |
      |                                   |                                                                                                       |
      |                                   | Range: 5-300. Default value: **10**.                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+
      | Response Codes                    | The HTTP codes used to check for a successful response from a target.                                 |
      |                                   |                                                                                                       |
      |                                   | Set this parameter only when **Protocol** is not set to **TCP**.                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------+

#. Click **OK**.
