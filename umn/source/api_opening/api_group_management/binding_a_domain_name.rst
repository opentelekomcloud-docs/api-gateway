:original_name: apig-en-ug-180327076.html

.. _apig-en-ug-180327076:

Binding a Domain Name
=====================

Scenario
--------

Before you open an API, you must bind one or more independent domain names to the group to which the API belongs.

.. note::

   -  In a dedicated gateway, you cannot bind the same independent domain name to different API groups.

Note the following points before you bind a domain name:

-  Subdomain name: After an API group is created, the system automatically allocates a unique subdomain name to it for internal testing. The subdomain name can be accessed 1000 times a day, but it cannot be modified.
-  Independent domain name: You can add five custom domain names for API callers to call your open APIs. There is no limit on the number of times these domain names can be accessed.

Prerequisites
-------------

#. There is an independent domain name available.

#. Dedicated gateway: An A record points the independent domain name to the address of the gateway. For details, see section "Adding an A Record Set" in the *Domain Name Service User Guide*.

#. .. _apig-en-ug-180327076__en-us_topic_0103545823_li8423956164017:

   If the API group contains APIs that are called through HTTPS, there needs to be SSL certificates configured for the independent domain name. SSL certificates can only be added manually with a custom name, content, and a key.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **API Groups**.

#. Go to the **Domain Names** tab page using one of the following methods:

   -  Click the name of the target API group, and click the **Domain Names** tab on the displayed API group details page.
   -  In the **Operation** column of the target API group, choose **More** > **Manage Domain Name**.

#. Click **Bind Independent Domain Name** and enter a domain name.

   For API groups created under dedicated gateways, specify the minimum TLS version (TLS 1.1 or TLS 1.2) supported by domain names that you bind to the API groups. TLS 1.2 is recommended.

#. Click **OK**.

   If the domain name is not needed, click **Unbind** to unbind it from the API group.

#. (Optional) If the API group contains APIs that are accessed through HTTPS, add an SSL certificate.

   a. Click **Add SSL Certificate**.
   b. Enter the name, content, and key of the :ref:`obtained SSL certificate <apig-en-ug-180327076__en-us_topic_0103545823_li8423956164017>`, and click **OK**.

   .. note::

      -  Currently, you can only add SSL certificates in the PEM format. To add SSL certificates of other formats, convert the certificates into the PEM format first.
      -  To replace or edit an SSL certificate, click |image1| next to the certificate name. The certificate content and key will not be visible after you click **OK** to add the certificate. If the content has been updated, add the entire content or key again.
      -  If you do not require an SSL certificate, click **Delete SSL Certificate** in the row containing the certificate to delete it.

Troubleshooting
---------------

-  Failure in binding an independent domain name: The independent domain name is not CNAMEd to the subdomain name of the API group, or the independent domain name already exists.
-  Failure in adding an SSL certificate: The domain name of the SSL certificate is different from the domain name for which you add the SSL certificate.

Follow-Up Operations
--------------------

After binding independent domain names to the API group, create APIs in the group to selectively expose backend capabilities. For details, see :ref:`Creating an API <apig-en-ug-180307020>`.

.. |image1| image:: /_static/images/en-us_image_0000001188830213.png
