:original_name: apig_03_0005.html

.. _apig_03_0005:

Creating an API Group
=====================

An API group contains APIs used for the same service. You can manage APIs by group, and must create a group before creating an API.

You can create an API group using the following methods:

-  :ref:`Creating an API Group Directly <apig_03_0005__en-us_topic_0000001175975942_en-us_topic_0089184725_en-us_topic_0080101677_section8731554122615>`

   You can create APIs for the group as required.

-  :ref:`Importing an API Design File <apig_03_0005__en-us_topic_0000001175975942_section1427163464212>`

   Import an API file to create a group.

-  Importing a CCE Workload

   By importing Cloud Container Engine (CCE) workloads, you can open up your CCE service capabilities. For details, see :ref:`Importing a CCE Workload <apig_03_0071>`.

.. note::

   -  To make your APIs available for users to access, bind independent domain names to the group to which the APIs belong.
   -  Each API can belong to only one group.
   -  The system automatically allocates a subdomain name to each API group for internal testing. The subdomain name can be accessed 1000 times a day. **You can also disable the Debugging Domain Name switch. When disabled, the debugging domain name is hidden and APIs cannot be called through it.**
   -  API group **DEFAULT** is automatically generated for each gateway. APIs in this group can be called using the IP address of the Virtual Private Cloud (VPC) where the gateway is deployed.

Prerequisites
-------------

You have :ref:`created a gateway <apig_03_0037>`.

.. _apig_03_0005__en-us_topic_0000001175975942_en-us_topic_0089184725_en-us_topic_0080101677_section8731554122615:

Creating an API Group Directly
------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.
#. Choose **API Management** > **API Groups**.
#. Choose **Create API group** > **Create Directly**, and enter group information.

   .. table:: **Table 1** Group information

      =========== =============================
      Parameter   Description
      =========== =============================
      Name        API group name.
      Description Description of the API group.
      =========== =============================

#. Click **OK**.

.. _apig_03_0005__en-us_topic_0000001175975942_section1427163464212:

Importing an API Design File
----------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.
4. Choose **Create API Group** > **Import API Design File**.
5. Select an API file and click **Open**.
6. Set the import parameters.

   .. table:: **Table 2** Parameters for importing APIs

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================+
      | Import                            | Options:                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  **New group**: Import APIs to a new API group. If you select this option, the system automatically creates an API group and imports the APIs into this group.                               |
      |                                   | -  **Existing group**: Import APIs to an existing API group. If you select this option, the system adds the APIs to the selected API group while retaining the existing APIs in the API group. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API group                         | Select an API group if you set **Import** to **Existing group**.                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Basic Definition Overwrite        | Determine whether to overwrite an existing API if the name of the API is the same as that of an imported API.                                                                                  |
      |                                   |                                                                                                                                                                                                |
      |                                   | This parameter is available only if you set **Import** to **Existing group**.                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Extended Definition Overwrite     | If this option is selected, the extended definition items (access control and request throttling policies) of an imported API will overwrite the existing policies with the same name.         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. (Optional) To configure the APIs, click **Configure Global Settings**.

   a. Change the authentication mode. For details, see :ref:`5.b <apig_03_0010__en-us_topic_0000001176135914_li6358122832510>`.
   b. Modify the backend request configuration. For details, see :ref:`1 <apig_03_0010__en-us_topic_0000001176135914_en-us_topic_0000001126143529_li12956182663810>`.
   c. Click **Next**. You can view the configuration details in form, JSON, or YAML format.
   d. Confirm the settings and click **Submit**.

8. Click **Import Now**, and determine whether to publish the APIs.

   -  **Now**: Publish the APIs in a specified environment now.
   -  **Later**: :ref:`Publish the APIs <apig_03_0014>` later.

9. Click **OK**. The **APIs** tab is displayed, showing the imported APIs.

Follow-Up Operations
--------------------

After an API group is created, :ref:`bind independent domain names <apig_03_0006>` to it so that API callers can use them to call open APIs in the group.
