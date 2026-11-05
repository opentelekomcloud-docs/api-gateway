:original_name: apig_03_0006.html

.. _apig_03_0006:

Configuring the Domain Name for Calling APIs
============================================

The domain name for calling APIs includes the debugging domain name and independent domain name. The debugging domain name is an internal domain name automatically allocated by the system for testing after an API group is created. It can be accessed for a maximum of 1,000 times per day. When opening an API, you need to bind an independent domain name to the API group so that users can access APIs in the API group using the independent domain name.

Independent domain names are classified into private and public domain names.

-  Private domain name: Service systems deployed on the cloud service platform can use private domain names to access APIs.
-  Public domain name: Service systems deployed outside the cloud service platform can use public domain names to access APIs.

If the independent domain name you select is a wildcard domain name (for example, **\*.aaa.com**), you can use any of its subdomain names (for example, **default.aaa.com** and **1.aaa.com**) to access all APIs in the group to which the domain name is bound.

.. _apig_03_0006__section53771439658:

Constraints
-----------

-  By default, the debugging domain name of an API group can only be resolved to a server in the same VPC as the gateway. If you want to resolve the domain name to a public network, bind an EIP to the gateway.
-  The debugging domain name is for debugging only, not for production.
-  A maximum of five independent domain names can be added to each group. The number of access times of each domain name is not limited.
-  Groups under the same gateway cannot be bound with a same independent domain name.
-  If a domain name is already bound to a port, it cannot be bound to the same port again.
-  If different ports are used for the same domain name, all ports take effect no matter whether any of them are bound to, modified, or unbound from the SSL certificate or whether client authentication is enabled or disabled.
-  If you access backend services through a load balance channel, the port bound to the independent domain name must be the same as the :ref:`access port of the backend server <apig_03_0040>` in the load balance channel.
-  After an independent domain name is bound to a port, if you use an IP address to access an API in a custom group, you need to add the header parameter **host** to the request. The **host** value should include the port number for access, unless you are using the default port **80** or **443**, in which case the **host** value is optional.
-  Accessing APIs by IP address is not advised, it requires IP certificates for SSL. Otherwise, the connection may be insecure.
-  HTTP-to-HTTPS redirection is only suitable for GET and HEAD requests. Redirecting other requests may cause data loss due to browser restrictions. Redirection takes effect only when the API request protocol is **HTTPS** or **HTTP&HTTPS** and an SSL certificate has been bound to the independent domain name.
-  **\*.aaa.com** can match domain names such as **default.aaa.com**, **1.aaa.com**, and **1.2.aaa.com**. However, if the domain name of a certificate is **\*.aaa.com**, the certificate can be used only for **default.aaa.com** and **1.aaa.com**, it cannot be used for **1.2.aaa.com**.

.. _apig_03_0006__section47514124459:

Obtaining Domain Names
----------------------

#. Apply for a domain name.

   -  To enable a service system on the cloud service platform to access APIs, obtain a **private domain name** as an independent domain name. For details, see `Creating a Private Zone <https://docs.otc.t-systems.com/en-us/usermanual/dns/en-us_topic_0057773658.html>`__.
   -  To enable a service system outside the cloud service platform to access APIs, obtain a **public domain name** as an independent domain name. You can apply for it from the domain name registrar.

2. .. _apig_03_0006__li159317403455:

   Configure domain name resolution for the independent domain name.

   -  If you use an independent private domain name, add an **A record set** of the VPC access address of the gateway or an **CNAME record set** of the debugging domain name of the API group to the domain name. For details, see `Record Set Types and Configuration Rules <https://docs.otc.t-systems.com/en-us/usermanual/dns/dns_usermanual_0601.html>`__.
   -  If you use an independent public domain name, add an **A record set of the gateway EIP** or a CNAME record set of the debugging domain name of the API group. For details, see `Record Set Types and Configuration Rules <https://docs.otc.t-systems.com/en-us/usermanual/dns/dns_usermanual_0601.html>`__.

3. If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name bound to the group. Obtain the content and keys of the SSL certificate and :ref:`create an SSL certificate <apig_03_0055>` in advance.

Binding an Independent Domain Name
----------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.
#. Choose **API Management** > **API Groups**.
#. Click a group name to go to the **Group Information** page.
#. In the **Independent Domain Names** area, click **Bind Independent Domain Name**.
#. Set the parameters according to the following table.

   .. table:: **Table 1** Independent domain name configuration

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================================================================================================+
      | Domain Name                       | :ref:`Domain name to be bound to the API group <apig_03_0006__section47514124459>`.                                                                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Minimum TLS Version               | Transport Layer Security (TLS) is a security protocol used to ensure security and data integrity for Internet communication. Select the minimum TLS version used for domain name access. TLS1.1 and TLS1.2 (recommended) are supported. TLS1.0 and TLS1.3 are not supported.                             |
      |                                   |                                                                                                                                                                                                                                                                                                          |
      |                                   | This parameter applies only to HTTPS and does not take effect for HTTP and other access modes. Configure HTTPS cipher suites using the **ssl_ciphers** parameter on the :ref:`Parameters <apig_03_0039>` tab.                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HTTP-to-HTTPS Auto Redirection    | HTTP APIs are insecure in transmission and authentication. You can upgrade them for access over HTTPS while ensuring HTTP compatibility.                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                          |
      |                                   | Redirection takes effect only when the API request protocol is **HTTPS** or **HTTP&HTTPS** and an SSL certificate has been bound to the independent domain name. **Redirection is only suitable for GET and HEAD requests. Redirecting other requests may cause data loss due to browser restrictions.** |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HTTP Port                         | The default value is **80**, which is the default HTTP port number. You can customize the inbound port. For details, see :ref:`Customizing Gateway Inbound Ports <apig_03_0109>`. If the HTTP port is not used, select **suspend**.                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HTTPS Port                        | The default value is **443**, which is the default HTTPS port. You can customize the inbound port. For details, see :ref:`Customizing Gateway Inbound Ports <apig_03_0109>`. If the HTTPS port is not used, select **suspend**.                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   -  If the domain name is displayed in the domain name list, the domain name is created successfully.
   -  If the domain name is no longer needed, click **Unbind Domain Name** to unbind it from the API group.
   -  If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name. For details, see :ref:`(Optional) Binding an SSL Certificate <apig_03_0006__section929954502012>`.

.. _apig_03_0006__section929954502012:

(Optional) Binding an SSL Certificate
-------------------------------------

If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name bound to the group. Otherwise, skip this step.

#. In the row that contains the domain name, click **Add SSL Certificate**.
#. Select an SSL certificate and click **OK**.

   -  If a CA certificate has been uploaded for the SSL certificate, you can enable client authentication (HTTPS two-way authentication). **Enabling or disabling client authentication will affect the existing services. Exercise caution when performing this operation.**
   -  If no SSL certificate is available, click **Create SSL Certificate** to create one. For details, see :ref:`Adding an SSL Certificate for an API <apig_03_0055>`.

Related Documents
-----------------

FAQs about configuring the domain name for calling APIs:

-  Failure in binding a domain name: :ref:`The domain name is not resolved <apig_03_0006__li159317403455>` or the domain name already exists.
-  Failure in binding an SSL certificate: The domain name used to generate the SSL certificate is different from the target independent domain name.
