:original_name: apig-en-ug-180307033.html

.. _apig-en-ug-180307033:

Adding an Excluded App or Tenant
================================

Scenario
--------

If you want to control the number of API calls received from a specific app or tenant, add an excluded app or tenant to a request throttling policy.

Prerequisites
-------------

You have created an app or obtained an app ID of another account or an account ID.

Adding an Excluded App
----------------------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **Request Throttling**.
#. Click the name of the target request throttling policy.
#. On the displayed request throttling policy details page, click the **Excluded Apps** tab.
#. Click **Select Excluded App**.
#. Select an app to exclude. You can use one of the following methods:

   -  To select an existing app, click **Existing**, select an app, and enter a threshold.
   -  To select an app of other tenants, click **Cross-tenant**, and enter the app ID and a threshold.

      .. note::

         Excluded app thresholds take precedence over the value of **Max. App Requests**.

         For example, a request throttling policy has been configured, with **Max. API Requests** being **10**, **Max. App Requests** being **3**, **Period** being 1 minute, and two excluded apps (max. **2** API requests for app A and max. **4** API requests for app B). If the request throttling policy is bound to an API, apps A and B can access the API 2 and 4 times within 1 minute, respectively.

Adding an Excluded Tenant
-------------------------

#. Log in to the management console.

#. Hover the mouse pointer over the username, click the username, and choose **My Credentials** from the drop-down list.

#. .. _apig-en-ug-180307033__en-us_topic_0084226147_li785710139335:

   On the **My Credentials** page, view the account ID and project ID.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **Request Throttling**.

#. Click the name of the target request throttling policy.

#. Click the **Excluded Tenants** tab.

#. Click **Select Excluded Tenant**.

#. In the **Select Excluded Tenant** dialog box, set the parameters listed in :ref:`Table 1 <apig-en-ug-180307033__en-us_topic_0084226147_table10544879441>`.

   .. _apig-en-ug-180307033__en-us_topic_0084226147_table10544879441:

   .. table:: **Table 1** Excluded tenant configuration

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                  |
      +===================================+==============================================================================================================+
      | Account ID                        | Account ID or project ID obtained in :ref:`3 <apig-en-ug-180307033__en-us_topic_0084226147_li785710139335>`. |
      |                                   |                                                                                                              |
      |                                   | -  Enter a project ID if you will bind or have bound this policy to an API that uses app authentication.     |
      |                                   | -  Enter an account ID if you will bind or have bound this policy to an API that uses IAM authentication.    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------+
      | Threshold                         | The maximum number of times an API can be called by the tenant within a specified period.                    |
      |                                   |                                                                                                              |
      |                                   | The value of this parameter cannot exceed that of **Max. API Requests**.                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   .. note::

      Excluded tenant thresholds take precedence over the value of **Max. User Requests**.

      For example, suppose a request throttling policy is configured, with **Max. API Requests** being **10**, **Max. User Requests** being **3**, **Period** being 1 minute, and two excluded tenants (max. **2** API requests for tenant A and max. **4** API requests for tenant B). If the request throttling policy is bound to an API, tenants A and B can access the API 2 and 4 times within 1 minute, respectively.
