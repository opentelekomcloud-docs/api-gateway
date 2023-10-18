:original_name: apig-en-ug-180307049.html

.. _apig-en-ug-180307049:

Creating an App and Obtaining Authorization
===========================================

Scenario
--------

For an API that uses app authentication, you can create an app and use the app and its ID and key pair (AppKey and AppSecret) to call the API. You can use an app to call an API only after you bind the app to the API. When you call the API, replace the key pair in the SDK with your own key pair so that APIG can authenticate your identity. For details about app authentication, see *Developer Guide*.

.. note::

   -  If the authentication mode of the target API has been set to **None** or **IAM**, you do not need to create apps to call this API.

Creating an App
---------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Calling** > **Apps**.

#. Click **Create App**, and configure the app information.

   .. table:: **Table 1** App information

      =========== =======================
      Parameter   Description
      =========== =======================
      Name        App name.
      Description Description of the app.
      =========== =======================

   .. note::

      You can customize AppKeys and AppSecrets on dedicated gateways. An AppKey is an identifier and must be globally unique. It is automatically generated. You are not advised to customize one unless it is necessary.

#. Click **OK**.

   After the app is created, its name and ID are displayed in the app list.

#. Click the app name, and view the AppKey and AppSecret on the app details page.

Binding an App to an API
------------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Calling** > **Apps**.

#. Bind an app to an API. You can use one of the following methods:

   -  In the **Operation** column of the app, click **Bind to API**, and then click **Select API**.
   -  Click the name of the target app, and click **Select API**.

#. Select an environment, select an API, and click **OK**.

   After the binding is complete, you can view the API on the app details page.

   .. note::

      -  Only APIs using app authentication can be bound with apps.
      -  An app can be bound to multiple APIs that use app authentication, and each such API can be bound with multiple apps.
      -  To debug an API to which the app is bound, click **Debug** in the row containing the API.

Follow-Up Operations
--------------------

You can call APIs using different authentication methods. For details, see :ref:`Calling APIs <apig-ug-0011>`.
