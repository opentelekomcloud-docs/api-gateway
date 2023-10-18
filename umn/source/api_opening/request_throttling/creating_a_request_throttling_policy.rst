:original_name: apig-en-ug-180307029.html

.. _apig-en-ug-180307029:

Creating a Request Throttling Policy
====================================

Scenario
--------

Request throttling controls the number of times an API can be called within a time period to protect backend services.

To provide stable, uninterrupted services, you can create request throttling policies to control the number of calls made to your APIs.

Request throttling policies take effect for an API only if they have been bound to the API.

.. note::

   -  An API can be bound with only one request throttling policy for a given environment, but each request throttling policy can be bound to multiple APIs.
   -  For a dedicated gateway, the limit is the value of **ratelimit_api_limits** you have configured on the **Configuration Parameters** page.

Prerequisites
-------------

You have :ref:`published the API <apig-en-ug-180307023>` to which you want to bind a request throttling policy.


Creating a Request Throttling Policy
------------------------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **Request Throttling**.

#. Click **Create Request Throttling Policy**, and set the parameters listed in :ref:`Table 1 <apig-en-ug-180307029__table1496031175119>`.

   .. _apig-en-ug-180307029__table1496031175119:

   .. table:: **Table 1** Parameters for creating a request throttling policy

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================+
      | Name                              | Request throttling policy name.                                                                                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | API-based or API-shared request throttling.                                                                                                                                              |
      |                                   |                                                                                                                                                                                          |
      |                                   | -  **API-based**: Request throttling is based on every API to which the policy is bound.                                                                                                 |
      |                                   | -  **API-shared**: Request throttling is based on all APIs as a whole to which the policy is bound.                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Period                            | For how long you want to limit the number of API calls. This parameter can be used together with the following parameters:                                                               |
      |                                   |                                                                                                                                                                                          |
      |                                   | -  **Max. API Requests**: Limit the maximum number of times an API can be called within a specific period.                                                                               |
      |                                   | -  **Max. User Requests**: Limit the maximum number of times an API can be called by a user within a specific period.                                                                    |
      |                                   | -  **Max. App Requests**: Limit the maximum number of times an API can be called by an app within a specific period.                                                                     |
      |                                   | -  **Max. IP Address Requests**: Limit the maximum number of times an API can be called by an IP address within a specific period.                                                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. API Requests                 | The maximum number of times each bound API can be called within the specified period.                                                                                                    |
      |                                   |                                                                                                                                                                                          |
      |                                   | This parameter must be used together with **Period**.                                                                                                                                    |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. User Requests                | The maximum number of times each bound API can be called by a user within the specified period. **This limit only applies to APIs that are accessed through app or IAM authentication.** |
      |                                   |                                                                                                                                                                                          |
      |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                              |
      |                                   | -  This parameter must be used together with **Period**.                                                                                                                                 |
      |                                   | -  If there are many users under your account that access an API, the request throttling limits of the API will apply to all these users.                                                |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. App Requests                 | The maximum number of times each bound API can be called by an app within the specified period. **This limit only applies to APIs that are accessed through app authentication.**        |
      |                                   |                                                                                                                                                                                          |
      |                                   | -  The value of this parameter cannot exceed that of **Max. User Requests**.                                                                                                             |
      |                                   | -  This parameter must be used together with **Period**.                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. IP Address Requests          | The maximum number of times each bound API can be called by an IP address within the specified period.                                                                                   |
      |                                   |                                                                                                                                                                                          |
      |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                              |
      |                                   | -  This parameter must be used together with **Period**.                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the request throttling policy.                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   After the policy is created, it is displayed on the **Request Throttling** page. You can bind this policy to APIs to throttle API requests.

Binding a Request Throttling Policy to an API
---------------------------------------------

#. Go to the page for binding a request throttling policy to an API. You can use one of the following methods:

   -  In the **Operation** column of the request throttling policy to be bound, click **Bind to API**, and then click **Select API**.
   -  Click the name of the target request throttling policy, and click **Select API** on the **APIs** tab page.

#. Specify an API group, environment, and API name keyword to search for the desired API.
#. Select the API and click **OK**.

   .. note::

      If a request throttling policy is no longer needed for an API, you can unbind it. To unbind a request throttling policy from multiple APIs, select the APIs, and click **Unbind**. You can unbind a request throttling policy from a maximum of 1000 APIs at a time.

Follow-Up Operations
--------------------

To control the maximum number of API calls received from a specific app or tenant, specify the app or tenant to exclude by referring to :ref:`Adding an Excluded App or Tenant <apig-en-ug-180307033>`. If an app is excluded in a request throttling policy, any threshold configured for that app takes precedence over the request throttling policy. The API and user request limits of this policy are still valid. If a tenant is excluded in a request throttling policy, any threshold configured for that tenant will be applied. The API and app request limits of this policy are still valid.
