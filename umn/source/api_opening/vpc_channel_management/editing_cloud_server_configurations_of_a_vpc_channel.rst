:original_name: apig-en-ug-180502087.html

.. _apig-en-ug-180502087:

Editing Cloud Server Configurations of a VPC Channel
====================================================

Scenario
--------

You can add or remove cloud servers and edit cloud server weights for VPC channels to meet service requirements.

Prerequisites
-------------

You have created a VPC channel.

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **VPC Channels**.
#. Click the name of the target VPC channel.
#. Click the **Cloud Servers** tab.
#. Add or remove cloud servers and edit cloud server weights.

   -  Adding cloud servers

      a. Click **Select Cloud Server**.
      b. Select the cloud servers you want to add, set cloud server weights, and click **OK**.

         .. note::

            To ensure a successful health check and service availability, configure the security groups of the backend cloud servers to allow access from 100.125.0.0/16.

   -  Removing cloud servers

      a. In the **Operation** column of the cloud servers you want to remove, click **Remove**.
      b. Click **Yes**.

   -  Editing the weight of a cloud server

      a. In the **Weight** column of the target cloud server, click |image1|.
      b. Change the weight and click |image2|.

   -  Editing the weights of multiple cloud servers

      a. Select the cloud servers to be edited, and click **Edit Weight**.
      b. Change the weights of the selected cloud servers, and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001188838057.png
.. |image2| image:: /_static/images/en-us_image_0000001142758142.png
