:original_name: apig_03_0056.html

.. _apig_03_0056:

Configuring Authentication Credentials
======================================

APIs that use App authentication require a credential to call. Create a credential to generate an ID and key/secret pair. These APIs can be called only when credentials are bound to them. During API calling, the key/secret pair is configured in the SDK and APIG can authenticate your identity based on the key/secret pair.

.. note::

   APIs that use IAM, custom authentication or require no authentication do not need credentials.

Prerequisites
-------------

You have created an API using app authentication. If no API is created, create one by performing steps provided in :ref:`Creating an API <apig_03_0128>`.

Constraints
-----------

-  You can create a maximum of 50 credentials for each gateway. A credential can be bound to a maximum of 1,000 APIs.
-  A credential can be bound to multiple APIs that use app authentication, and each such API can be bound with multiple credentials.

Creating a Credential
---------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.
4. Click **Create Credential** and configure parameters based on the following table.

   .. table:: **Table 1** Credential information

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================+
      | Name                              | Credential name. It can contain 3 to 64 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                   |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the credential. Enter 1 to 255 characters.                                                                                                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Configuration              | You can create a custom AppKey and AppSecret. **However, we recommend using the automatically generated keys and secrets (visible in your credential details) unless you have specific needs.**                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AppKey                            | Credential key. It is an identifier and must be globally unique. The value can contain 8 to 200 characters, including letters, digits, underscores (_), and hyphens (-), and must start with a letter or digit.                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AppSecret                         | Credential secret. It is used for identity authentication. The value can contain 8 to 128 characters, including letters, digits, underscores (_), hyphens (-), and special characters: !@#%. The value must start with a letter or digit. |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | The secret of a credential can be reset. For details, see :ref:`Resetting Secret <apig_03_0056__section19872617202717>`.                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

5. Click **OK**.

   -  If the credential is displayed in the credential list, the credential is successfully created.
   -  Click the credential name and view the key and secret.

6. Bind/Authorize the credential to an API so that the API can be called through app authentication. For details, see :ref:`Binding/Authorizing Credentials to APIs <apig_03_0056__section179331518155613>`.

.. _apig_03_0056__section179331518155613:

Binding/Authorizing Credentials to APIs
---------------------------------------

APIG can authenticate the identity and call the associated API based on the key/secret pair of the credential.

**Binding a credential to APIs**

#. On the **Credentials** page, click the name of the target credential.

#. In the **APIs** area, click **Select APIs**.

#. Select an environment, API group, and APIs.

#. Click **OK**.

   To unbind an API, click **Unbind** in the row that contains the API.

**Authorizing credentials to an API**

5. In the navigation pane, choose **API Management** > **API Groups**.

6. Click a group name to go to the **Group Information** page.

7. On the **APIs** tab, select the target API and choose **More** > **Authorize Credentials**.

8. Click **Select Credentials**.

9. Select an environment, search for and select desired credentials, and click **OK**. The authorized credentials are displayed on the **Authorize Credentials** page.

   To cancel the authorization of a credential, click **Cancel Authorization** in the **Operation** column that contains the credential.

.. _apig_03_0056__section19872617202717:

Resetting Secret
----------------

Each credential key is unique and cannot be reset. Credential secrets can be reset. After a secret is reset, the original secret becomes invalid, and the API bound to the credential cannot be called. In this case, you need to update the key pair in the SDK and call the API again.

#. In the navigation pane, choose **API Management** > **Credentials**.

2. Click the name of the target credential.
3. Click **Reset Secret**.
4. Click **OK**.

Related Documents
-----------------

-  After the API authentication credential is created, you can select the app authentication type based on service requirements to call APIs. For details, see :ref:`Calling an Open API <apig_03_0046>`.
-  If you select the simple authentication for App authentication, you need to create an AppCode. For details, see :ref:`Configuring AppCodes for Simple Authentication <apig_03_0058>`.
