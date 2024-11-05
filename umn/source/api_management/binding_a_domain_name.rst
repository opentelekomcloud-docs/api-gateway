:original_name: apig_03_0006.html

.. _apig_03_0006:

Binding a Domain Name
=====================

Before you expose an API, bind an independent domain name to the API group so that APIs in the group can be accessed with the domain name. A maximum of five independent domain names can be added, and the number of access times is not limited.

Independent domain names are classified into private and public domain names.

-  Private domain name: Service systems deployed on the cloud service platform can use private domain names to access APIs.
-  Public domain name: Service systems deployed outside the cloud service platform can use public domain names to access APIs.

For internal testing, use the debugging domain name (subdomain name) to access APIs in an API group (maximum 1,000 times a day). The debugging domain name cannot be modified.

.. note::

   -  Groups under the same gateway cannot be bound with a same independent domain name.
   -  By default, the debugging domain name of an API group can only be resolved to a server in the same VPC as the gateway. If you want to resolve the domain name to a public network, bind an EIP to the gateway.
   -  If the independent domain name you select is a wildcard domain name (for example, **\*.aaa.com**), you can use any of its subdomain names (for example, **default.aaa.com** and **1.aaa.com**) to access all APIs in the group to which the domain name is bound.

Obtaining Domain Names
----------------------

-  To enable a service system on the cloud service platform to access APIs, obtain a private zone as an independent domain name.

   #. Apply for a private network domain name. For details, see `Creating a Private Zone <https://docs.otc.t-systems.com/en-us/usermanual/dns/en-us_topic_0057773658.html>`__
   #. Configure an A record set to map the domain name to the APIC address. For details, see `Adding an A Record Set <https://docs.otc.t-systems.com/en-us/usermanual/dns/dns_usermanual_0007.html>`__
   #. If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name bound to the group. Obtain the content and keys of the SSL certificate and :ref:`create an SSL certificate <apig_03_0055>` in advance.

-  To enable a service system outside the cloud service platform to access APIs, obtain a public zone as an independent domain name.

   #. Apply for a public zone from Domain Registration.
   #. Configure a CNAME record set for the API group subdomain name. For details, see `Adding a CNAME Record Set <https://docs.otc.t-systems.com/en-us/usermanual/dns/dns_usermanual_0010.html>`__.
   #. If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name bound to the group. Obtain the content and keys of the SSL certificate and :ref:`create an SSL certificate <apig_03_0055>` in advance.

Procedure
---------

#. Go to the APIG console.

#. Select a dedicated gateway at the top of the navigation pane.

#. Choose **API Management** > **API Groups**.

#. Click a group name.

#. Click the **Group Information** tab.

#. In the **Independent Subdomain Names** area, click **Bind Independent Domain Name**. Then configure the domain name information.

   .. table:: **Table 1** Independent domain name configuration

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================+
      | Domain Name                       | Domain name to be bound to the API group.                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Minimum TLS Version               | The minimum TLS version that can be used to access the domain name. TLS 1.1 and TLS 1.2 (recommended) are supported.                                                                                          |
      |                                   |                                                                                                                                                                                                               |
      |                                   | This parameter applies only to HTTPS and does not take effect for HTTP and other access modes. Configure HTTPS cipher suites using the **ssl_ciphers** parameter on the :ref:`Parameters <apig_03_0039>` tab. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HTTP-to-HTTPS Auto Redirection    | Whether to support HTTP-to-HTTPS redirection.                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                               |
      |                                   | Redirection takes effect only when the API request protocol is **HTTPS** or **HTTP&HTTPS** and an SSL certificate has been bound to the independent domain name.                                              |
      |                                   |                                                                                                                                                                                                               |
      |                                   | .. note::                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    Redirection is only suitable for GET and HEAD requests. Redirecting other requests may cause data loss due to browser restrictions.                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   If the domain name is no longer needed, click **Unbind Domain Name** to unbind it from the API group.

#. .. _apig_03_0006__en-us_topic_0000001221574215_en-us_topic_0103545823_li93451675213:

   (Optional) If the API group contains HTTPS APIs, bind an SSL certificate to the independent domain name.

   a. In the row that contains the domain name, click **Select SSL Certificate**.

   b. Select an SSL certificate and click **OK**.

      -  If a CA certificate has been uploaded for the SSL certificate, you can enable client authentication (HTTPS two-way authentication). **Enabling or disabling client authentication will affect the existing services. Exercise caution when performing this operation.**
      -  If no SSL certificate is available, click **Create SSL Certificate** to create one. For details, see :ref:`SSL Certificates <apig_03_0055>`.

Troubleshooting
---------------

-  Failure in binding an independent domain name: It already exists or is not CNAMEd to the debugging domain name of the API group.
-  Failure in binding an SSL certificate: The domain name used to generate the SSL certificate is different from the target independent domain name.

Follow-Up Operations
--------------------

After binding independent domain names to the API group, create APIs in the group to selectively expose backend capabilities. For details, see :ref:`Creating an API <apig_03_0010>`.
