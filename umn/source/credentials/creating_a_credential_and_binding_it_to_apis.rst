:original_name: apig_03_0056.html

.. _apig_03_0056:

Creating a Credential and Binding It to APIs
============================================

For APIs that use app authentication, create credentials to generate credential IDs and key/secret pairs. When calling such an API, bind a credential to the API, use the key/secret pair to replace that in the SDK so that APIG can authenticate your identity. For details about app authentication, see the *API Gateway Developer Guide*.

.. note::

   -  APIs that use IAM, custom authentication or require no authentication do not need credentials.
   -  You can create a maximum of 50 credentials for each gateway.

Creating a Credential
---------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **Credentials**.
4. Click **Create Credential** and set credential information.

   .. table:: **Table 1** Credential information

      =========== =================================
      Parameter   Description
      =========== =================================
      Name        Credential name.
      Description Description about the credential.
      =========== =================================

   .. note::

      You can customize AppKeys (keys) and AppSecrets (secrets). An AppKey is an automatically generated identifier, which is globally unique. You are not advised to customize one unless it is necessary.

5. Click **OK**.

   -  After the credential is created, its name and ID are displayed on the **Credentials** page.
   -  Click the credential name and view the key and secret.

Binding a Credential to APIs
----------------------------

#. On the **Credentials** page, click the name of the target credential.

#. In the **APIs** area, click **Bind to APIs**.

#. Select an environment, API group, and APIs.

#. Click **OK**.

   To unbind an API, click **Unbind** in the row that contains the API.

   .. note::

      A credential can be bound to multiple APIs that use app authentication, and each such API can be bound with multiple credentials.
