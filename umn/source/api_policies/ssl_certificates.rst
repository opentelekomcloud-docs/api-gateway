:original_name: apig_03_0055.html

.. _apig_03_0055:

SSL Certificates
================

API groups that contain HTTPS-compatible APIs must have their independent domain names bound with SSL certificates. SSL certificates are used for data encryption and identity verification, and support both one-way and two-way authentication.

-  One-way authentication: When connecting to the server, a client verifies whether the server is correct.

   |image1|

-  Two-way authentication: When connecting to a server, a client verifies the server and the server also verifies the client.

   |image2|

Prerequisites
-------------

-  Only SSL certificates in PEM format are supported.
-  SSL certificates support only the RSA, ECDSA, and DSA encryption algorithms.

Adding an SSL Certificate
-------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.
#. In the navigation pane, choose **API Management** > **API Policies**.
#. On the **SSL Certificates** tab, click **Create SSL Certificate**.

   .. table:: **Table 1** SSL certificate configuration

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter an SSL certificate name that conforms to specific rules to facilitate search.                                                                                                                                                                                                                                                                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Gateways Covered                  | -  **Current**: The certificate will be displayed only for the current gateway.                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  **All**: The certificate will be displayed for all gateways.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Content                           | SSL certificate content in PEM format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | Open the target PEM certificate file using Notepad or other tools, and copy the certificate content to **Content**.                                                                                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | If the certificate is not in PEM format, :ref:`convert it to this format <apig_03_0055__en-us_topic_0000001239951831_section79831962193>`.                                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key                               | SSL certificate key in PEM format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | Open the KEY or PEM private key file using Notepad or other tools, and copy the private key to **Key**.                                                                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | CA                                | For two-way authentication, you need to enter the CA certificate to verify both the server and client certificates. After the CA certificate is uploaded, the independent domain name needs to be bound to an :ref:`SSL certificate <apig_03_0006__en-us_topic_0000001221574215_en-us_topic_0103545823_li93451675213>` to enable two-way authentication. Open the CA certificate file (.pem format) corresponding to the preceding certificate content as a text file and copy the CA content to **CA**. |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | If the certificate is not in PEM format, :ref:`convert it to this format <apig_03_0055__en-us_topic_0000001239951831_section79831962193>`.                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    If your gateway does not support CA certificates, contact customer service to upgrade the gateway.                                                                                                                                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. The SSL certificate is added.

.. _apig_03_0055__en-us_topic_0000001239951831_section79831962193:

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

Updating an SSL Certificate
---------------------------

On the certificate list page, locate the certificate to be updated, click **Modify** in the **Operation** column, and modify the certificate information.

-  Updating the SSL certificate does not affect API calling.
-  If the certificate to be updated has been bound to an independent domain name, all clients that access the domain name can view the updated certificate.
-  If the updated SSL certificate has been bound to an independent domain name, the client authentication (HTTPS two-way authentication) is disabled by default when a CA certificate is added to the updated content.

Follow-Up Operations
--------------------

After creating a certificate, :ref:`bind it <apig_03_0006__en-us_topic_0000001221574215_en-us_topic_0103545823_li93451675213>` to an independent name of an API group.

.. |image1| image:: /_static/images/en-us_image_0000001475355676.png
.. |image2| image:: /_static/images/en-us_image_0000001485758705.png
