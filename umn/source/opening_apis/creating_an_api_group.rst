:original_name: apig_03_0005.html

.. _apig_03_0005:

Creating an API Group
=====================

An API group contains APIs used for the same service. You can manage APIs by group, and must create a group before creating an API.

You can create an API group using the following methods:

-  Creating an API Group Directly

   You can create APIs for the group as required. For details, see :ref:`Creating an API group <apig_03_0005__en-us_topic_0089184725_en-us_topic_0080101677_section8731554122615>`.

-  Importing an API Design File

   Import an API design file to create a group. For details, see :ref:`Importing APIs through an API Design File <apig_03_0067>`.

-  Importing a CCE Workload

   By importing Cloud Container Engine (CCE) workloads, you can open your CCE service capabilities. During the import, an API group can be created. For details, see :ref:`Importing APIs Through CCE Workloads <apig_03_0071>`.

Constraints
-----------

-  Each API can belong to only one group.
-  The system automatically allocates a subdomain name to each API group for internal testing. The subdomain name can be accessed 1000 times a day. You can also disable the Debugging Domain Name switch on the Group Information page in the console. When disabled, the debugging domain name is hidden and APIs cannot be called through it.
-  The debugging domain name is for debugging only, not for production. You are advised to use a :ref:`dedicated domain name <apig_03_0006>`.
-  By default, the debugging domain name of an API group can only be resolved to a server in the same VPC as the gateway. If you want to resolve the domain name to a public network, bind an EIP to the gateway.

.. _apig_03_0005__en-us_topic_0089184725_en-us_topic_0080101677_section8731554122615:


Creating an API group
---------------------

#. Go to the APIG console.

#. Select a dedicated gateway at the top of the navigation pane.

#. Choose **API Management** > **API Groups**.

#. Choose **Create API group** > **Create Directly**, and enter group information based on the following table.

   .. table:: **Table 1** Group information

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                 |
      +===================================+=============================================================================================================================+
      | Name                              | API group name. Enter a name that conforms to specific rules to facilitate search.                                          |
      |                                   |                                                                                                                             |
      |                                   | Enter 3 to 255 characters, starting with a letter or digit. Use only letters, digits, and these special characters: -_./:() |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the API group. Enter 0 to 1,000 characters.                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   If the created API group is displayed in the API group list, the API group is created successfully.

Related Documents
-----------------

-  After an API group is created, you can bind an independent domain name to the group, add environment variables, and configure gateway responses. For details, see :ref:`Configuring the Domain Name for Calling APIs <apig_03_0006>`, :ref:`(Optional) Configuring the Environment and Environment Variables <apig_03_0007>`, and :ref:`Customizing Error Response for APIs <apig_03_0008>`.
-  Each gateway provides a DEFAULT group. You can call APIs in the default group using the VPC address. For details, see :ref:`Calling an Open API <apig_03_0046>`.
