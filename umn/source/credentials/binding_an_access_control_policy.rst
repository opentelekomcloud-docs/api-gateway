:original_name: apig_03_0060.html

.. _apig_03_0060:

Binding an Access Control Policy
================================

As a protection mechanism for backend services, access control policies control the client (API caller) IP addresses that can access APIs. You can bind an access control policy to allow or deny access of specified IP addresses to an API.

Procedure
---------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.
4. Click the name of the target credential.
5. In the **Access Control Policy** area, click **Bind**.
6. Configure the policy information.

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
