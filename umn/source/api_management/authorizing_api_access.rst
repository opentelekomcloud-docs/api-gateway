:original_name: apig_03_0013.html

.. _apig_03_0013:

Authorizing API Access
======================

APIs using app authentication can only be called by credentials that have been authorized to call them.

.. important::

   -  You can authorize credentials only to call APIs that use app authentication.
   -  A credential can be authorized to access a maximum of 1000 APIs.

Prerequisites
-------------

-  You have published an API.
-  You have created an environment.
-  You have created a credential.

Procedure
---------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.

4. Click a group name.

5. On the **APIs** tab, select the target API and choose **More** > **Authorize Credentials**.

6. Click **Select Credentials**.

7. Select an environment, search for and select desired credentials, and click **OK**. The authorized credentials are displayed on the **Authorize Credentials** page.

   To cancel the authorization of a credential, click **Cancel Authorization** in the **Operation** column that contains the credential.

Follow-Up Operations
--------------------

After you authorize a credential for an API, the API can be called by the credential using SDKs of different programming languages.
