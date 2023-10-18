:original_name: apig-en-ug-180307015.html

.. _apig-en-ug-180307015:

Creating an API Group
=====================

Scenario
--------

Before creating an API, you must create an API group. An API group contains different APIs used for the same service.

.. note::

   Each API can only belong to one API group.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **API Groups**.

#. Click **Create API Group**, and set the parameters described in :ref:`Table 1 <apig-en-ug-180307015__en-us_topic_0089184725_en-us_topic_0080101677_table195413315428>`.

   .. _apig-en-ug-180307015__en-us_topic_0089184725_en-us_topic_0080101677_table195413315428:

   .. table:: **Table 1** Parameters for creating an API group

      =========== =============================
      Parameter   Description
      =========== =============================
      Name        API group name.
      Description Description of the API group.
      =========== =============================

#. Click **OK**.

   After the API group is created, it is displayed in the API group list.

   .. note::

      -  The system automatically allocates a subdomain name to the API group for internal testing. The subdomain name can be accessed 1000 times a day.
      -  A default API group is automatically generated for each dedicated gateway. APIs in the default group can be called using the IP address of the VPC where the dedicated gateway is deployed.
      -  To make your APIs available for users to access, bind independent domain names to the API group to which the APIs belong.

Follow-Up Operations
--------------------

After the API group is created, bind independent domain names to it so that API callers can use the domain names to call APIs in the group. For more information, see :ref:`Binding a Domain Name <apig-en-ug-180327076>`.
