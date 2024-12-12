:original_name: apig_03_0059.html

.. _apig_03_0059:

Binding a Credential Quota Policy
=================================

A credential quota policy limits the number of API calls that a credential can make during a specified period.

Procedure
---------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.

4. Click the name of the target credential.

5. In the **Credential Quota Policies** area, click **Bind**.

6. Specify the policy type.

   -  **Existing policy**: Select a policy.
   -  **New policy**: Configure a policy by referring to :ref:`Table 1 <apig_03_0059__en-us_topic_0000001234554311_table11535115191017>`.

   .. _apig_03_0059__en-us_topic_0000001234554311_table11535115191017:

   .. table:: **Table 1** Credential quota policy configuration

      +-------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter         | Description                                                                                                                                                                                                                                                                                                                       |
      +===================+===================================================================================================================================================================================================================================================================================================================================+
      | Name              | Enter a credential quota policy name that conforms to specific rules to facilitate search.                                                                                                                                                                                                                                        |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Effective On      | Time when the quota policy takes effect. For example, if **Effective On** is set to **Aug 8, 2020 05:05:00** and **Period** is set to 1 hour, the quota policy takes effect on Aug 8, 2020 05:05:00. The period from the fifth minute of an hour to the fifth minute of the next hour is a cycle, for example, 05:05:00-06:05:00. |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Period            | Period in which the quota policy is applied. The unit can be second, minute, hour, or day. This parameter must be used along with **Max. API Requests** to limit the total number of times an API can be called by a client within the specified period.                                                                          |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. API Requests | The maximum number of times that an API can be called by a client. This parameter must be used along with **Period**.                                                                                                                                                                                                             |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description       | Description about the credential quota policy.                                                                                                                                                                                                                                                                                    |
      +-------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. After the configuring is complete, click **OK**.
