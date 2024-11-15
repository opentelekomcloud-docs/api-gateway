:original_name: apig_03_0025.html

.. _apig_03_0025:

Request Throttling
==================

Request throttling limits the number of times APIs can be called by a user or app within a specific time period to protect backend services. The throttling can be down to the minute or second. To ensure service continuity of an API, create a request throttling policy for the API.

Usage Guidelines
----------------

-  You have understood the :ref:`guidelines for policy creation and API binding <apig_03_0019__en-us_topic_0000001221774151_en-us_topic_0000001151883501_section126118109015>`.
-  Adding a request throttling policy to an API means binding them to each other. An API can be bound with only one request throttling policy for a given environment, but each request throttling policy can be bound to multiple APIs.
-  For APIs not bound with a request throttling policy, the throttling limit is the value of **ratelimit_api_limits** set on the **Parameters** page of the gateway.

Configuration Parameters
------------------------

.. table:: **Table 1** Configuration parameters

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                                                                                                                                                                   |
   +===================================+===============================================================================================================================================================================================================================+
   | Name                              | Request throttling policy name.                                                                                                                                                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Type                              | API-based or API-shared request throttling.                                                                                                                                                                                   |
   |                                   |                                                                                                                                                                                                                               |
   |                                   | -  **API-specific**: Request throttling is based on every API to which the policy is bound.                                                                                                                                   |
   |                                   | -  **API-sharing**: Request throttling is based on all APIs as a whole to which the policy is bound.                                                                                                                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Period                            | For how long you want to limit the number of API calls. This parameter can be used together with the following parameters:                                                                                                    |
   |                                   |                                                                                                                                                                                                                               |
   |                                   | -  **Max. API Requests**: Limit the maximum number of times an API can be called within a specific period.                                                                                                                    |
   |                                   | -  **Max. User Requests**: Limit the maximum number of times an API can be called by a user within a specific period.                                                                                                         |
   |                                   | -  **Max. Credential Requests**: Limit the maximum number of times an API can be called by a credential within a specific period.                                                                                             |
   |                                   | -  **Max. IP Address Requests**: Limit the maximum number of times an API can be called by an IP address within a specific period.                                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. API Requests                 | The maximum number of times each bound API can be called within the specified period.                                                                                                                                         |
   |                                   |                                                                                                                                                                                                                               |
   |                                   | This parameter must be used together with **Period**.                                                                                                                                                                         |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. User Requests                | The maximum number of times each bound API can be called by a user within the specified period. **This limit only applies to APIs that are accessed through app or IAM authentication.**                                      |
   |                                   |                                                                                                                                                                                                                               |
   |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                                                                   |
   |                                   | -  This parameter must be used together with **Period**.                                                                                                                                                                      |
   |                                   | -  If there are many users under your account that access an API, the request throttling limits of the API will apply to all these users.                                                                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. Credential Requests          | The maximum number of times each bound API can be called by a credential within the specified period. **This limit only applies to APIs that are accessed through app authentication.**                                       |
   |                                   |                                                                                                                                                                                                                               |
   |                                   | -  The value of this parameter cannot exceed that of **Max. User Requests** or **Max. API Requests**.                                                                                                                         |
   |                                   | -  This parameter must be used together with **Period**.                                                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Max. IP Address Requests          | Maximum times that an API can be requested by an IP address. You can configure the **real_ip_from_xff** parameter of the gateway to use the IP address in the **X-Forwarded-For** header as the basis for request throttling. |
   |                                   |                                                                                                                                                                                                                               |
   |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                                                                   |
   |                                   | -  This parameter must be used together with **Period**.                                                                                                                                                                      |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Description                       | Description of the request throttling policy.                                                                                                                                                                                 |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Follow-Up Operations
--------------------

-  To control the traffic of a credential, bind a request throttling policy to the credential by referring to :ref:`Binding a Request Throttling Policy to a Credential <apig_03_0025__en-us_topic_0000001176454394_section123605128317>`. Traffic of the credential is limited by the excluded credential threshold, while traffic of APIs and users are still limited by the request throttling policy.
-  To control the traffic of a tenant, bind a request throttling policy to the tenant by referring to :ref:`Binding a Request Throttling Policy to a Tenant <apig_03_0025__en-us_topic_0000001176454394_section28257147344>`. Traffic of the tenant is limited by the excluded tenant threshold, while traffic of APIs and users are still limited by the request throttling policy.

.. _apig_03_0025__en-us_topic_0000001176454394_section123605128317:

Binding a Request Throttling Policy to a Credential
---------------------------------------------------

You have created a credential or obtained a credential ID from other tenants.

#. On the request throttling policy details page, click the **Excluded Credentials** tab.
#. Click **Select Excluded Credential**.
#. Select a credential to exclude. You can use one of the following methods:

   -  To select an existing credential, click **Existing**, select a credential, and enter a threshold.
   -  To select a credential of other tenants, click **Cross-tenant**, and enter the credential ID and a threshold.

   .. note::

      Excluded credential thresholds take precedence over the value of **Max. Credential Requests**.

      For example, a request throttling policy has been configured, with **Max. API Requests** being **10**, **Max. Credential Requests** being **3**, **Period** being 1 minute, and two excluded credentials (max. **2** API requests for credential A and max. **4** API requests for credential B). If the request throttling policy is bound to an API, credential A and B can access the API 2 and 4 times within 1 minute, respectively.

.. _apig_03_0025__en-us_topic_0000001176454394_section28257147344:

Binding a Request Throttling Policy to a Tenant
-----------------------------------------------

#. On the request throttling policy details page, click the **Excluded Tenants** tab.

2. Click **Select Excluded Tenant**.
3. Enter the tenant information.

   .. table:: **Table 2** Excluded tenant configuration

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================+
      | Tenant ID                         | Account ID or project ID. For details, see the description about **Excluded Tenants** in :ref:`Table 1 <apig_03_0054__en-us_topic_0000001313537817_table3471155116443>`. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Threshold                         | The maximum number of times an API can be called by the tenant within a specified period.                                                                                |
      |                                   |                                                                                                                                                                          |
      |                                   | The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

4. Click **OK**.

   .. note::

      Excluded tenant thresholds take precedence over the value of **Max. User Requests**.

      For example, a request throttling policy has been configured, with **Max. API Requests** being **10**, **Max. User Requests** being **3**, **Period** being 1 minute, and two excluded tenants (max. **2** API requests for tenant A and max. **4** API requests for tenant B). If the request throttling policy is bound to an API, tenants A and B can access the API 2 and 4 times within 1 minute, respectively.
