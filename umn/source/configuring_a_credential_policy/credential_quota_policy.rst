:original_name: apig_03_0059.html

.. _apig_03_0059:

Credential Quota Policy
=======================

A credential quota limits the total number of times that an API can be called by a credential in a specified period to protect backend services. You can create a credential quota policy to limit the number of API calls made by credentials bound to the policy.

A credential quota policy and a credential are independent of each other. The policy takes effect on the credential only after the credential is bound to the policy.

Creating a Credential Quota Policy
----------------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.

4. Click the name of the target credential.

5. In the **Credential Quota Policy** area, click **Bind**.

6. Specify the policy type.

   -  **Existing policy**: Select a policy.
   -  **New policy**: Configure a policy by referring to :ref:`Table 1 <apig_03_0059__table11535115191017>`.

   .. _apig_03_0059__table11535115191017:

   .. table:: **Table 1** Credential quota policy configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter a credential quota policy name that conforms to specific rules to facilitate search.                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effective On                      | Time when the quota policy takes effect. For example, if **Effective On** is set to **Aug 8, 2020 05:05:00** and **Period** is set to 1 hour, the quota policy takes effect on Aug 8, 2020 05:05:00. The period from the fifth minute of an hour to the fifth minute of the next hour is a cycle, for example, 05:05:00-06:05:00. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Period                            | Time window for quota measurement. Maximum number of times an API can be called within the period. Unit: second, minute, hour, or day.                                                                                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. API Requests                 | Maximum number of times that an API can be called by a client within the time window specified by **Period**. Range: 1 to 2,147,483,647.                                                                                                                                                                                          |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the credential quota policy. Enter 1 to 255 characters.                                                                                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. After the configuring is complete, click **OK**.

   -  If the policy is displayed in the **Credential Quota Policy** area, the policy is successfully created.
   -  To unbind a credential quota policy, click **Unbind**.
   -  To delete a credential quota policy, click **Bind**, and click **Delete** in the row containing the policy.

Related Documents
-----------------

An API request throttling policy controls the global traffic, while a credential quota policy controls the quota of a single user. The two policies can be used together.

-  Credential quota policy: sets a call quota for a single credential (AppCode) to limit the number of calls made using the credential within a specified period. This policy controls the resource consumption of a single user.
-  API request throttling policy: sets a global traffic limit for a single API to restrict the total number of API calls made by all callers within a specified period. This policy ensures the stability of backend services. For details about API request throttling policies, see :ref:`Configuring API Request Throttling <apig_03_0025>` and :ref:`Request Throttling 2.0 <apig_03_0054>`.
