:original_name: apig_03_0025.html

.. _apig_03_0025:

Configuring API Request Throttling
==================================

Request throttling controls the number of times APIs can be called by user, credential, time range, or other dimensions to protect the backend services. The throttling can be accurate to the minute or second. To provide stable, uninterrupted services, you can configure request throttling policies to control the number of calls made to your APIs.

Constraints
-----------

-  Adding a request throttling policy to an API means binding them to each other. An API can be bound with only one request throttling policy for a given environment, but each request throttling policy can be bound to multiple APIs.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating a Request Throttling Policy
------------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **Request Throttling** in the **Traditional Policy** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** Request throttling parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================================================================+
      | Name                              | Request throttling policy name. It can contain 3 to 64 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | API-based or API-shared request throttling.                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                           |
      |                                   | -  **API-specific**: Request throttling is based on every API to which the policy is bound.                                                                                                                                                                                               |
      |                                   | -  **API-sharing**: Request throttling is based on all APIs as a whole to which the policy is bound.                                                                                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Period                            | The throttling can be accurate to the second, minute, hour, or day.                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                           |
      |                                   | -  **Max. API Requests**: Limit the maximum number of times an API can be called within a specific period.                                                                                                                                                                                |
      |                                   | -  **Max. User Requests**: Limit the maximum number of times an API can be called by a user within a specific period.                                                                                                                                                                     |
      |                                   | -  **Max. Credential Requests**: Limit the maximum number of times an API can be called by a credential within a specific period.                                                                                                                                                         |
      |                                   | -  **Max. IP Address Requests**: Limit the maximum number of times an API can be called by an IP address within a specific period.                                                                                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. API Requests                 | The maximum number of times each bound API can be called within the specified period.                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                           |
      |                                   | -  If no request throttling policy is bound to an API, the maximum number of API calls is determined by the value of **ratelimit_api_limits** (see :ref:`Configuring Gateway Parameters <apig_03_0039>`). **ratelimit_api_limits** specifies the global default request throttling limit. |
      |                                   | -  The value of **Max. API Requests** cannot exceed that of **ratelimit_api_limits**.                                                                                                                                                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. User Requests                | The maximum number of times each bound API can be called by a user within the specified period. **This limit only applies to APIs that are accessed through app or IAM authentication.**                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                           |
      |                                   | -  The value of **Max. User Requests** cannot exceed that of **Max. API Requests**.                                                                                                                                                                                                       |
      |                                   | -  If there are many users under your account that access an API, the request throttling limits of the API will apply to all these users.                                                                                                                                                 |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Credential Requests          | The maximum number of times each bound API can be called by a credential within the specified period. **This limit only applies to APIs that are accessed through app authentication.**                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                           |
      |                                   | The value of **Max. Credential Requests** cannot exceed that of **Max. User Requests** and **Max. API Requests**.                                                                                                                                                                         |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. IP Address Requests          | Maximum times that an API can be requested by an IP address. You can configure the :ref:`real_ip_from_xff <apig_03_0039>` parameter of the gateway and use the IP address in the **X-Forwarded-For** header as the basis for request throttling.                                          |
      |                                   |                                                                                                                                                                                                                                                                                           |
      |                                   | The value of **Max. IP Address Requests** cannot exceed that of **Max. API Requests**.                                                                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the request throttling policy. Enter 1 to 255 characters.                                                                                                                                                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the created request throttling policy is displayed in the policy list, the policy is created successfully.
   -  To control the traffic of a credential, bind a request throttling policy to the credential by referring to :ref:`Configuring Excluded Credentials for a Request Throttling Policy <apig_03_0025__section6161162412298>`.
   -  To control the traffic of a tenant, bind a request throttling policy to the tenant by referring to :ref:`Configuring Excluded Tenants for a Request Throttling Policy <apig_03_0025__section716172420290>`.

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0025__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

.. _apig_03_0025__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.

.. _apig_03_0025__section6161162412298:

Configuring Excluded Credentials for a Request Throttling Policy
----------------------------------------------------------------

If you want to throttle requests for a credential, you can add an excluded credential to the request throttling policy. The **Max. Credential Requests** of the credential will then be restricted by the threshold of the excluded credential, while **Max. API Requests** and **Max. User Requests** are restricted by the throttling policy.

#. On the request throttling policy details page, click the **Excluded Credentials** tab.
#. Click **Select Excluded Credential**.
#. Select a credential to exclude. You can use one of the following methods:

   -  To select an existing credential, click **Existing**, select a credential, and enter a threshold.
   -  To select a credential of other tenants, click **Cross-tenant**, and enter the credential ID and a threshold.

   .. note::

      Excluded credential thresholds take precedence over the value of **Max. Credential Requests**.

      For example, a request throttling policy has been configured, with **Max. API Requests** being **10**, **Max. Credential Requests** being **3**, **Period** being 1 minute, and two excluded credentials (max. **2** API requests for credential A and max. **4** API requests for credential B). If the request throttling policy is bound to an API, credential A and B can access the API 2 and 4 times within 1 minute, respectively.

.. _apig_03_0025__section716172420290:

Configuring Excluded Tenants for a Request Throttling Policy
------------------------------------------------------------

If you want to throttle requests for a tenant, you can add an excluded tenant to the request throttling policy. After the tenant is added to the request throttling policy, **Max. User Requests** of the tenant is limited by the threshold of the excluded tenant, and **Max. API Requests** and **Max. App Requests** are limited by the throttling policy.

#. On the request throttling policy details page, click the **Excluded Tenants** tab.

2. Click **Select Excluded Tenant**.
3. Set the parameters according to the following table.

   .. table:: **Table 2** Excluded tenant configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================+
      | Tenant ID                         | **Tenant ID**: an account ID or project ID.                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Specify a project ID for an API with app authentication. For details, see `Obtaining a Project ID <https://docs.otc.t-systems.com/en-us/api/apig/apig-api-180713009.html>`__.                                      |
      |                                   | -  Specify an account ID (not IAM user ID) for an API with IAM authentication. For details, see `Obtaining an Account Name and Account ID <https://docs.otc.t-systems.com/en-us/api/apig/apig-api-180713005.html>`__. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Threshold                         | Throttling threshold allowed for a tenant within a specified period.                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

4. Click **OK**.

   .. note::

      Excluded tenant thresholds take precedence over the value of **Max. User Requests**.

      For example, a request throttling policy has been configured, with **Max. API Requests** being **10**, **Max. User Requests** being **3**, **Period** being 1 minute, and two excluded tenants (max. **2** API requests for tenant A and max. **4** API requests for tenant B). If the request throttling policy is bound to an API, tenants A and B can access the API 2 and 4 times within 1 minute, respectively.

Related Documents
-----------------

Error codes

+------------+--------------------------------------------+------------------+--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Error Code | Error Message                              | HTTP Status Code | Description                                | Solution                                                                                                                                                                                 |
+============+============================================+==================+============================================+==========================================================================================================================================================================================+
| APIG.0308  | The throttling threshold has been reached. | 429              | The throttling threshold has been reached. | Try again after the throttling resumes. If the maximum number of requests sent to an API (accessible using a debugging domain name) per day is reached, bind an independent domain name. |
+------------+--------------------------------------------+------------------+--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
