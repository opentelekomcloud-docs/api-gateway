:original_name: apig_03_0055.html

.. _apig_03_0055:

Adding an SSL Certificate for an API
====================================

If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name bound to the group. An SSL certificate is used for data encryption and identity authentication. Both one-way authentication and two-way authentication are supported. **If no SSL certificate is configured, the request security cannot be ensured. You are advised to configure an SSL certificate.**

-  One-way authentication: When connecting to the server, a client verifies whether the server is correct.

   |image1|

-  Two-way authentication: When connecting to a server, a client verifies the server and the server also verifies the client.

   |image2|

Constraints
-----------

-  Only SSL certificates in PEM format are supported.
-  SSL certificates support only the RSA and ECDSA encryption algorithms.

Prerequisites
-------------

-  You have obtained the SSL certificate.
-  If two-way authentication is used, you also need to obtain the CA certificate.

Adding an SSL Certificate
-------------------------

#. Go to the APIG console.

#. Select a dedicated gateway at the top of the navigation pane.

#. In the navigation pane, choose **API Management** > **API Policies**.

#. On the **SSL Certificates** tab, click **Create SSL Certificate**.

#. Configure the certificate according to the following table.

   .. table:: **Table 1** SSL certificate configuration

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter an SSL certificate name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | Enter 4 to 50 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Instances Covered                 | Certificate display scope.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Current**: The certificate will be displayed only for the current gateway.                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  **Global**: The certificate will be displayed for all gateways of the current account in the current region.                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Content                           | SSL certificate content in PEM format.                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  Open the target PEM certificate file using Notepad or other tools, and copy the certificate content to **Content**.                                                                                                                                                                                                                                                                                                                                     |
      |                                   | -  If the certificate is not in PEM format, :ref:`convert it to this format <apig_03_0055__section79831962193>`.                                                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key                               | SSL certificate key in PEM format.                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | Open the KEY or PEM private key file using Notepad or other tools, and copy the private key to **Key**.                                                                                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | CA                                | For two-way authentication, you need to enter the CA certificate to verify both the server and client certificates. After the CA certificate is uploaded, the independent domain name needs to be bound to an :ref:`SSL certificate <apig_03_0006__section929954502012>` to enable two-way authentication. Open the CA certificate file (.pem format) corresponding to the preceding certificate content as a text file and copy the CA content to **CA**. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      |                                   | -  If the certificate is not in PEM format, :ref:`convert it to this format <apig_03_0055__section79831962193>`.                                                                                                                                                                                                                                                                                                                                           |
      |                                   | -  If the current gateway does not support CA certificates, contact technical support to upgrade it.                                                                                                                                                                                                                                                                                                                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   If the created certificate is displayed in the certificate list, the certificate is created successfully.

#. After creating a certificate, bind it to an independent name of an API group. For details, see :ref:`(Optional) Binding an SSL Certificate <apig_03_0006__section929954502012>`.

   To modify a certificate, see :ref:`Updating an SSL Certificate <apig_03_0055__section19661152172210>`.

.. _apig_03_0055__section79831962193:

Converting Certificate Format to PEM
------------------------------------

+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| Format                            | Converting with `OpenSSL <https://www.openssl.org/>`__                                                                               |
+===================================+======================================================================================================================================+
| CER/CRT                           | Rename the certificate file **cert.crt** **cert.pem**.                                                                               |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| PFX                               | -  Run the private key export command. For example, run the following command to convert **cert.pfx** into **key.pem**:              |
|                                   |                                                                                                                                      |
|                                   |    openssl pkcs12 -in cert.pfx -nocerts -out key.pem                                                                                 |
|                                   |                                                                                                                                      |
|                                   | -  Run the certificate export command. For example, run the following command to convert **cert.pfx** into **cert.pem**:             |
|                                   |                                                                                                                                      |
|                                   |    openssl pkcs12 -in cert.pfx -nokeys -out cert.pem                                                                                 |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| P7B                               | #. Run the certificate conversion command. For example, run the following command to convert **cert.p7b** into **cert.cer**:         |
|                                   |                                                                                                                                      |
|                                   |    openssl pkcs7 -print_certs -in cert.p7b -out cert.cer                                                                             |
|                                   |                                                                                                                                      |
|                                   | #. Rename the certificate file **cert.cer** **cert.pem**.                                                                            |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+
| DER                               | -  Run the private key export command. For example, run the following command to convert **privatekey.der** into **privatekey.pem**: |
|                                   |                                                                                                                                      |
|                                   |    openssl rsa -inform DER -outform PEM -in privatekey.der -out privatekey.pem                                                       |
|                                   |                                                                                                                                      |
|                                   | -  Run the certificate export command. For example, run the following command to convert **cert.cer** into **cert.pem**:             |
|                                   |                                                                                                                                      |
|                                   |    openssl x509 -inform der -in cert.cer -out cert.pem                                                                               |
+-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------+

.. _apig_03_0055__section19661152172210:

Updating an SSL Certificate
---------------------------

On the certificate list page, locate the certificate to be updated, click **Modify** in the **Operation** column, and modify the certificate information.

-  Updating the SSL certificate does not affect API calling.
-  If the certificate to be updated has been bound to an independent domain name, all clients that access the domain name can view the updated certificate.
-  If the updated SSL certificate has been bound to an independent domain name, the client authentication (HTTPS two-way authentication) is disabled by default when a CA certificate is added to the updated content.

.. |image1| image:: /_static/images/en-us_image_0000001475355676.png
.. |image2| image:: /_static/images/en-us_image_0000001485758705.png
