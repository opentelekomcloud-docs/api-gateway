:original_name: apig_03_0028.html

.. _apig_03_0028:

Configuring Signature Verification for Backend Services
=======================================================

Signature keys are used by backend services to verify the identity of APIG.

A signature key consists of a key and secret, and can be used only after being bound to an API. When an API bound with a signature key is called, APIG adds signature details to the API request. The backend service of the API signs the request in the same way, and verifies the identity of APIG by checking whether the signature is consistent with that in the **Authorization** header sent by APIG.

|image1|

Constraints
-----------

-  An API can only be bound with one signature key in a given environment, but each signature key can be bound to multiple APIs.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating a Signature Key Policy
-------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **Signature Key** in the **Traditional Policy** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** Signature key parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Signature key name. It contains 3 to 64 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Authentication type. Options: **HMAC**, **Basic auth**, and **AES**.                                                                                                                                                                                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Signature Algorithm               | Select an AES signature algorithm. Options:                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  aes-128-cfb                                                                                                                                                                                                                                                                                                                                                           |
      |                                   | -  aes-256-cfb                                                                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Key                               | Set the key based on the signature key type you have selected.                                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  If **Type** is **HMAC**, enter the key of the key pair used for app authentication. It contains 8 to 32 characters, including letters, digits, underscores (_), and hyphens (-). Start with a letter or digit.                                                                                                                                                        |
      |                                   | -  If **Type** is **Basic auth**, enter the username used for basic authentication. It contains 4 to 32 characters, including letters, digits, hyphens (-), and underscores (_). Start with a letter or digit.                                                                                                                                                           |
      |                                   | -  If **Type** is set to **AES**, enter the key used for AES authentication. It includes letters, digits, and special characters: ``_-!@#$%+/=.`` Start with a letter, digit, plus sign (+), or slash (/). If the signature algorithm is **aes-128-cfb**, the key contains 16 characters. If the signature algorithm is **aes-256-cfb**, the key contains 32 characters. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Secret                            | Enter the secret information based on the key type you have selected.                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  If **Type** is **HMAC**, enter the secret of the key pair used for app authentication. It contains 16 to 64 characters, including letters, digits, and special characters: ``_-!@#$%.`` Start with a letter or digit.                                                                                                                                                 |
      |                                   | -  If **Type** is **Basic auth**, enter the password used for basic authentication. It contains 8 to 64 characters, including letters, digits, and special characters: ``_-!@#$%.`` Start with a letter or digit.                                                                                                                                                        |
      |                                   | -  If **Type** is **AES**, enter the vector used for AES authentication. It contains 16 characters, including letters, digits, and special characters: ``_-!@#$%+/=.`` Start with a letter, digit, plus sign (+), or slash (/).                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Secret                    | Enter the secret again.                                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   If the policy is displayed in the policy list, the policy is successfully created.

8. After the policy is created, perform the operations described in :ref:`Binding a Policy to APIs <apig_03_0028__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

.. _apig_03_0028__section20100104416176:

Binding a Policy to APIs
------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   If an API no longer needs this policy, click **Unbind** in the row that contains the API.

.. |image1| image:: /_static/images/en-us_image_0000002107833988.png
