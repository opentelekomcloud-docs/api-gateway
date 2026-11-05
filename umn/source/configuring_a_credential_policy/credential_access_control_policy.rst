:original_name: apig_03_0060.html

.. _apig_03_0060:

Credential Access Control Policy
================================

Credential access control protects backend services by controlling API access from certain IP addresses. You can configure an access policy to allow or forbid the access of an API by a specified IP address using credentials.

Configuring a Credential Access Control Policy
----------------------------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.

4. Click the name of the target credential.

5. In the **Access Control Policy** area, click **Bind**.

6. Set the parameters according to the following table.

   .. table:: **Table 1** Access control policy configuration

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                       |
      +===================================+===================================================================================================================+
      | Effect                            | Access control type. Options:                                                                                     |
      |                                   |                                                                                                                   |
      |                                   | -  **Allow**: Only clients with specified IP addresses are allowed to call APIs to which the credential is bound. |
      |                                   | -  **Deny**: Clients with specified IP addresses are not allowed to call APIs to which the credential is bound.   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | IP Addresses                      | Click **Add IP Address** to add IP addresses.                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------+

7. After the configuring is complete, click **OK**.

   If the policy is displayed in the **Access Control Policy** area, the policy is successfully created.
