:original_name: apig-en-ug-180307021.html

.. _apig-en-ug-180307021:

Authorizing Apps to Call an API
===============================

Scenario
--------

APIs using app authentication can only be called by apps that have been authorized to call them.

.. note::

   -  You can only authorize apps to call published APIs.
   -  You can authorize apps only to call APIs that use app authentication.

Prerequisites
-------------

-  You have created an API group and API.
-  (Optional) You have created an environment.
-  You have created an app.

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **APIs**.
#. Authorize apps to call an API. You can use one of the following methods:

   -  In the **Operation** column of the target API, choose **More** > **Authorize App**, and then click **Select App**.
   -  Select the target API, click **Authorize App** over the API list, and then click **Select App**.
   -  Authorize apps through the API details page.

      a. Click the name of the target API.
      b. Click the **Authorization** tab.
      c. Click **Select App**.

   .. note::

      To authorize an app to access multiple APIs, select the APIs, and click **Authorize App**. Click **Select App**, select the app you wish to authorize, and click **OK**. You can grant access to a maximum of 1000 APIs at a time.

#. Select an environment, search for and select desired apps, and click **OK**.
#. After the authorization is complete, view the authorized apps on the **Authorization** tab page or the **Authorize App** page.

   .. note::

      If an app does not need to call the API, click **Cancel Authorization** in the row containing the app to unbind it.

Follow-Up Operations
--------------------

After you authorize an app to call an API, the API can be called using SDKs of different programming languages.
