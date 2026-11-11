:original_name: apig_03_0060.html

.. _apig_03_0060:

Credential Access Control Policy
================================

If an API can be called only by clients with specific IP addresses, you can configure an access control policy for the credential. By setting an IP address whitelist or blacklist, you can allow or deny access to the API from clients with specified IP addresses, thereby protecting backend services.

Configuring a Credential Access Control Policy
----------------------------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.
4. Click the name of the target credential.
5. In the **Access Control Policy** area, click **Bind**.
6. Set the parameters according to the following table.

   .. table:: **Table 1** Access control policy configuration

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                               |
      +===================================+===========================================================================================================================================+
      | Effect                            | Select the access control action. Default action: **Deny**.                                                                               |
      |                                   |                                                                                                                                           |
      |                                   | -  **Allow**: Only clients with specified IP addresses are allowed to call APIs to which the credential is bound.                         |
      |                                   | -  **Deny**: Clients with specified IP addresses are not allowed to call APIs to which the credential is bound.                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
      | IP Addresses                      | Click **Add IP Address** to add the client IP addresses or IP address segments that are allowed or forbidden to call an API.              |
      |                                   |                                                                                                                                           |
      |                                   | -  IP addresses support the following formats:                                                                                            |
      |                                   |                                                                                                                                           |
      |                                   |    -  Common IP address, for example, **127.0.0.1** or **::1**.                                                                           |
      |                                   |    -  IP address and mask, for example, **192.145.0.0/16** or **2407:c080:17ef:ffff:: 3104:703a/64**.                                     |
      |                                   |    -  IP address segment, for example, **127.0.0.1-192.145.0.1** or **2407:c080:17ef:ffff:: 3104:703a-2407:c080:17ef:ffff:: 3104: 704a**. |
      |                                   |                                                                                                                                           |
      |                                   | -  Before entering an IPv6 address, check whether the gateway supports IPv6 access.                                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+

7. After the configuring is complete, click **OK**.

   -  If the policy is displayed in the **Access Control Policy** area, the policy is successfully created.
   -  To unbind or delete a credential access control policy, click **Delete**.

Related Documents
-----------------

API access control controls the global IP address access permissions, and credential access control controls the IP address access permissions of a single credential. The two functions can be used together.

-  Credential access control: sets an IP address whitelist or blacklist for a single credential (AppCode) to allow or deny clients with specified IP addresses to access the API using the credential. This helps implement differentiated IP address control for different credentials.
-  API access control: sets an IP address whitelist or blacklist for a single API to allow or deny clients with specified IP addresses to call the API. This function takes effect for all credentials that call the API, ensuring the security of backend services. For details about API access control, see :ref:`Configuring API Access Control <apig_03_0027>`.
