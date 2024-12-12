:original_name: apig-faq-180307008.html

.. _apig-faq-180307008:

Can Applications Deployed in a VPC Call APIs?
=============================================

Yes, applications deployed in a VPC can call APIs by default. If domain name resolution fails, configure a DNS server on the current endpoint by following the instructions in :ref:`Configuring an Intranet DNS Server <apig-faq-180307008__en-us_topic_0000001130933972_en-us_topic_0089872475_section856622113118>`. After the configuration, applications deployed in the VPC can call APIs.

.. _apig-faq-180307008__en-us_topic_0000001130933972_en-us_topic_0089872475_section856622113118:

Configuring an Intranet DNS Server
----------------------------------

To configure a DNS server, specify its IP address in the **/etc/resolv.conf** file.

The IP address of the intranet DNS server depends on which region you are located in. Find the IP address of the intranet DNS server in your region from the private DNS server addresses mentioned in "FAQs" of the *Domain Name Service User Guide*.

Add an intranet DNS server with either of the following two methods:

-  Method 1: Modify the subnet information of the VPC.
-  Method 2: Edit the **/etc/resolv.conf** file.

   .. note::

      The intranet DNS server configurations become invalid after the ECS restarts, and the intranet DNS server must be configured again. Therefore, method 1 is recommended.

Method 1
--------

Perform the following procedure to add a DNS server IP address to the subnet configurations of the ECS in the VPC.

#. Log in to the management console.

#. Click |image1| in the upper left corner to select a region.

#. In the service list, choose **Compute** > **Elastic Cloud Server**.

#. Click the name of the ECS you want to use.

#. .. _apig-faq-180307008__en-us_topic_0000001130933972_en-us_topic_0089872475_li16910204134212:

   On the **Network Interfaces** tab page, click |image2| to view the subnet name.

#. On the **Summary** tab page, view the VPC name.

#. Click the VPC name to visit the VPC console.

#. Choose **Subnets** in the left navigation pane.

#. Locate the subnet mentioned in :ref:`5 <apig-faq-180307008__en-us_topic_0000001130933972_en-us_topic_0089872475_li16910204134212>` and click the subnet name.

#. Change the DNS server address of the subnet and click **OK**.

   For example, change the address to **100.125.1.250**.

#. Restart the ECS. Check that the **/etc/resolv.conf** file contains the IP address of the DNS server to be configured, and the IP address is less than those of all other DNS servers.

   The following figure shows the IP address **100.125.1.250** of the DNS server to be configured.

   |image3|

   .. note::

      Modifying the subnet information of a VPC will affect all ECSs created using the subnet.

Method 2
--------

Add the IP address of the intranet DNS server to the **/etc/resolv.conf** file.

For example, if you are located in **region01**, add an intranet DNS server of IP address **100.125.1.250** to the **/etc/resolv.conf** file.

.. note::

   -  The IP address of the new DNS server must be less than those of all other DNS servers.
   -  The DNS configurations take effect immediately after the **/etc/resolv.conf** file is saved.

.. |image1| image:: /_static/images/en-us_image_0143929918.png
.. |image2| image:: /_static/images/en-us_image_0000001143167164.png
.. |image3| image:: /_static/images/en-us_image_0000001189007099.png
