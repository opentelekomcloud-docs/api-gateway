:original_name: apig_03_0075.html

.. _apig_03_0075:

Configuring Gateway Tags
========================

Tags classify your gateways to facilitate search, analysis, and management.

You can search, analyze, and manage your resources on the `Tag Management Service (TMS) <https://docs.otc.t-systems.com/en-us/usermanual/tms/en-us_topic_0071335169.html>`__ console.

Constraints
-----------

A maximum of 20 tags can be added to a gateway.


Configuring Gateway Tags
------------------------

#. Go to the APIG console.

#. In the navigation pane, choose **Gateways**.

#. Click **Access Console** or the name of the target gateway.

#. On the **Tags** tab, click **Add Tag**.

   A tag consists of a key and value. The value can be empty.

   -  The key can contain letters, digits, and spaces in UTF-8 format. The following special characters are also allowed: ``_.:=+-@.`` Do not enter tags starting with **\_sys\_**, which are system tags.
   -  The value can contain letters, digits, and spaces in UTF-8 format. The following special characters are also allowed: \_.:=+-@

#. Click **OK**.

Viewing Gateways by Tag
-----------------------

Use the tags to filter, view, analyze, and manage your gateway resources on the TMS console.

#. Hover over icon on the left to expand the service list, and enter **TMS**.
#. On the TMS console, enter the required information to filter gateway resources.

   a. **Region**: Select the region where the gateway is located.
   b. **Resource Type**: Select **APIG**.
   c. **Resource Tag**: Select a tag key.
