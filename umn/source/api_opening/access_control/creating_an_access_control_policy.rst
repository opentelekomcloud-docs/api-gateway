:original_name: apig-en-ug-180712097.html

.. _apig-en-ug-180712097:

Creating an Access Control Policy
=================================

Scenario
--------

Access control policies are a type of security measures provided by APIG. You can use them to allow or deny API access from specific IP addresses or accounts.

Access control policies take effect for an API only if they have been bound to the API.

.. note::

   Each API can be bound with only one access control policy for a given environment, but each access control policy can be bound to multiple APIs.


Creating an Access Control Policy
---------------------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **Access Control**.

#. Click **Create Access Control Policy**.

#. In the **Create Access Control Policy** dialog box, set the parameters listed in :ref:`Table 1 <apig-en-ug-180712097__table56117818541>`.

   .. _apig-en-ug-180712097__table56117818541:

   .. table:: **Table 1** Parameters for creating an access control policy

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================================+
      | Name                              | Access control policy name.                                                                                                                                                                 |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Restriction Type                  | Type of the source from which API calls are to be controlled.                                                                                                                               |
      |                                   |                                                                                                                                                                                             |
      |                                   | -  **IP address**: Specify IP addresses and IP address ranges that are allowed or not allowed to access an API.                                                                             |
      |                                   | -  **Account name**: Specify names of the accounts that are allowed or not allowed to access an API.                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effect                            | Options: **Allow** and **Deny**.                                                                                                                                                            |
      |                                   |                                                                                                                                                                                             |
      |                                   | Use this parameter along with **Restriction Type** to control the access of certain IP addresses or accounts to an API.                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | IP Address                        | IP addresses and IP address ranges that are allowed or not allowed to access an API                                                                                                         |
      |                                   |                                                                                                                                                                                             |
      |                                   | You need to set this parameter only if you have set **Restriction Type** to **IP address**.                                                                                                 |
      |                                   |                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                             |
      |                                   |    You can set a maximum of 100 IP addresses respectively to allow or deny access.                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Account Names                     | Names of the accounts that are allowed or not allowed to access an API. **This parameter only applies to APIs that are accessed through IAM authentication.**                               |
      |                                   |                                                                                                                                                                                             |
      |                                   | You need to set this parameter only if you have set **Restriction Type** to **Account name**. You can enter multiple account names and separate them with commas, for example, **aaa,bbb**. |
      |                                   |                                                                                                                                                                                             |
      |                                   | .. note::                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                             |
      |                                   |    APIG performs access control on accounts, not IAM users created using accounts.                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. You can bind the policy to APIs to control API access.

Binding an Access Control Policy to an API
------------------------------------------

#. Go to the page for binding an access control policy to an API. You can use one of the following methods:

   -  In the **Operation** column of the access control policy to be bound, click **Bind to API**, and then click **Select API**.
   -  Click the name of the target access control policy, and click **Select API**.

#. Specify an API group, environment, and API name keyword to search for the desired API.
#. Select the API and click **OK**.

   .. note::

      If an access control policy is no longer needed for an API, you can unbind it from that API. To unbind an access control policy from multiple APIs, select the APIs, and click **Unbind**. You can unbind a request throttling policy from a maximum of 1000 APIs at a time.
