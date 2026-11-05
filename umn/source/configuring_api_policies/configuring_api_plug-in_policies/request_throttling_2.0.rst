:original_name: apig_03_0054.html

.. _apig_03_0054:

Request Throttling 2.0
======================

A request throttling 2.0 policy limits the number of times that an API can be called within a specific time period. Parameter-based, basic, and excluded throttling is supported.

-  Basic throttling

   Throttle requests by API, user, credential, or source IP address. This function is equivalent to a traditional request throttling policy (see :ref:`Configuring API Request Throttling <apig_03_0025>`) but is incompatible with it.

-  Parameter-based throttling

   Throttle requests based on headers, path parameter, method, query strings, or system parameters.

-  Excluded throttling

   Throttle requests based on specific credentials or tenants.

.. note::

   If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.

Constraints
-----------

-  An API can be bound with only one request throttling 2.0 policy for a given environment, but each request throttling 2.0 policy can be bound to multiple APIs.
-  A request throttling policy becomes invalid if a request throttling 2.0 policy is bound to the same API as the existing one.
-  A maximum of 100 rules can be defined for the parameter-based throttling.
-  The policy content cannot exceed 65,535 characters.
-  Policy parameters will be stored as plaintext. To prevent information leakage, do not contain sensitive information in these parameters.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating a Request Throttling 2.0 Policy
----------------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **Request Throttling 2.0** in the **Plug-ins** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** Request throttling 2.0 parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter a policy name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Fixed value: **Request Throttling 2.0**.                                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the plug-in. Enter 1 to 255 characters.                                                                                                                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Throttling                        | High-performance throttling is recommended.                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  **High precision**: better for low concurrency scenarios (performance is affected)                                                                                                                                                                                                                                                                                                  |
      |                                   | -  **High performance**: better for medium concurrency scenarios (performance is less affected, with small occasional errors)                                                                                                                                                                                                                                                          |
      |                                   | -  **Single node**: better for high concurrency scenarios (request throttling within each node; performance is least affected, with small occasional errors)                                                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Type                       | -  API-specific                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    Monitor and control the requests for a single API.                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  API-sharing                                                                                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    Monitor and control requests for all APIs bound with the policy.                                                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Period                            | The throttling can be accurate to the second, minute, hour, or day.                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Max. API Requests**: Limit the maximum number of times an API can be called within a specific period.                                                                                                                                                                                                                                                                             |
      |                                   | -  **Max. User Requests**: Limit the maximum number of times an API can be called by a user within a specific period.                                                                                                                                                                                                                                                                  |
      |                                   | -  **Max. Credential Requests**: Limit the maximum number of times an API can be called by a credential within a specific period.                                                                                                                                                                                                                                                      |
      |                                   | -  **Max. IP Address Requests**: Limit the maximum number of times an API can be called by an IP address within a specific period.                                                                                                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. API Requests                 | The maximum number of times each bound API can be called within the specified period.                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | This parameter must be used together with **Period**.                                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. User Requests                | The maximum number of times each bound API can be called by a user within the specified period. For APIs with IAM authentication, the throttling is based on a project ID; for APIs with app authentication, the throttling is based on an account ID. For details about account ID and project ID, see the description about **Excluded Tenants** in this table.                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                                                                                                                                                                                                                            |
      |                                   | -  This parameter must be used together with **Period**.                                                                                                                                                                                                                                                                                                                               |
      |                                   | -  If there are many users under your account that access an API, the request throttling limits of the API will apply to all these users.                                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Credential Requests          | The maximum number of times each bound API can be called by a credential within the specified period. This limit only applies to APIs that are accessed through app authentication.                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                                                                                                                                                                                                                            |
      |                                   | -  This parameter must be used together with **Period**.                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. IP Address Requests          | The maximum number of times each bound API can be called by an IP address within the specified period. You can configure the **real_ip_from_xff** parameter of the gateway and use the IP address in the **X-Forwarded-For** header as the basis for request throttling.                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  The value of this parameter cannot exceed that of **Max. API Requests**.                                                                                                                                                                                                                                                                                                            |
      |                                   | -  This parameter must be used together with **Period**.                                                                                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter-based Throttling        | Enable or disable parameter-based throttling. After this function is enabled, API requests are throttled based on the parameters you set.                                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameters                        | Define parameters for rule matching.                                                                                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Parameter Location**: the location of a parameter used for rule matching.                                                                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    -  **path**: API request URI. This parameter is configured by default.                                                                                                                                                                                                                                                                                                              |
      |                                   |    -  **method**: API request method. This parameter is configured by default.                                                                                                                                                                                                                                                                                                         |
      |                                   |    -  **header**: the key of a request header. **For security purposes, do not include sensitive information in these parameters.**                                                                                                                                                                                                                                                    |
      |                                   |    -  **query**: the key of a query string.                                                                                                                                                                                                                                                                                                                                            |
      |                                   |    -  **system**: a system parameter.                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  **Parameter**: the name of a parameter to match the specified value in a rule. The value can contain 1 to 32 characters and must start with a letter. Only letters, digits, hyphens (-), underscores (_), and periods (.) are allowed.                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rules                             | Define rules for request throttling to take effect.                                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | To add more rules, click **Add Rule**. Enter 3 to 255 characters, starting with a letter or digit. Use only letters, digits, and these special characters: -_./:()                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  Rules                                                                                                                                                                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    Click |image1| to set condition expressions. To set an expression, select a parameter and operator, and enter a value.                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    -  **=**: equal to                                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    -  **!=**: not equal to                                                                                                                                                                                                                                                                                                                                                             |
      |                                   |    -  **pattern**: regular expression                                                                                                                                                                                                                                                                                                                                                  |
      |                                   |    -  **enum**: enumerated values. Separate them with commas (,).                                                                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  Max. API Requests                                                                                                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    The maximum number of times that an API can be called within a specific time period.                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  Period                                                                                                                                                                                                                                                                                                                                                                              |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   |    A period of time that will apply with the throttling limit you set. If this parameter is not specified, the period set in the **Policy Information** area will be used.                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | For example, configure parameter-based throttling as follows: add the **Host** parameter and specify the location as **header**; add the condition **Host = www.abc.com**, and set the throttling limit to **10** and the period to 60s. For APIs whose **Host** parameter in the request header is equal to **www.abc.com**, they cannot be called again once called 10 times in 60s. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Excluded Throttling               | Enable or disable excluded throttling. After this function is enabled, the throttling limits for excluded tenants and credentials override the **Max. User Requests** and **Max. Credential Requests** set in the **Basic Throttling** area.                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Excluded Tenants                  | **Tenant ID**: an account ID or project ID.                                                                                                                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  Specify a project ID for an API with app authentication. For details, see `Obtaining a Project ID <https://docs.otc.t-systems.com/en-us/api/apig/apig-api-180713009.html>`__.                                                                                                                                                                                                       |
      |                                   | -  Specify an account ID (not IAM user ID) for an API with IAM authentication. For details, see `Obtaining an Account Name and Account ID <https://docs.otc.t-systems.com/en-us/api/apig/apig-api-180713005.html>`__.                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                        |
      |                                   | **Threshold**: the maximum number of times that a specific tenant can access an API within the specified period. The threshold cannot exceed the value of **Max. API Requests** in the **Basic Throttling** area.                                                                                                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Excluded Credentials              | Select a credential, and specify the maximum number of times that the credential can access an API within the specified period. The threshold cannot exceed the value of **Max. API Requests** in the **Basic Throttling** area.                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the policy is displayed in the policy list, the policy is created successfully.
   -  To clone this policy, click **Clone** in the **Operation** column. **The name of a cloned policy cannot be the same as that of any existing policy.**

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0054__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

Example Script
--------------

.. code-block::

   {
     "scope": "basic",
     "default_interval": 60,
     "default_time_unit": "second",
     "api_limit": 100,
     "app_limit": 50,
     "user_limit": 50,
     "ip_limit": 20,
     "specials": [
       {
         "type": "app",
         "policies": [
           {
             "key": "e9230d70c749408eb3d1e838850cdd23",
             "limit": 10
           }
         ]
       },
       {
         "type": "user",
         "policies": [
           {
             "key": "878f1b87f71c40a7a15db0998f358bb9",
             "limit": 10
           }
         ]
       }
     ],
     "algorithm": "counter",
     "parameters": [
       {
         "id": "3wuj354lpptv0toe0",
         "value": "reqPath",
         "type": "path",
         "name": "reqPath"
       },
       {
         "id": "53h7e7j11u38l3ocp",
         "value": "method",
         "type": "method",
         "name": "method"
       },
       {
         "id": "vv502bnb6g40td8u0",
         "value": "Host",
         "type": "header",
         "name": "Host"
       }
     ],
     "rules": [
       {
         "match_regex": "[\"Host\",\"==\",\"www.abc.com\"]",
         "rule_name": "u8mb",
         "time_unit": "second",
         "interval": 2,
         "limit": 5
       }
     ]
   }

.. _apig_03_0054__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.

Related Documents
-----------------

-  In addition to traditional request throttling policies, APIG provides request throttling 2.0 policies for more fine-grained throttling. For example, you can create a throttling 2.0 policy to handle gateway throttling in different scenarios. For details, see "Using Request Throttling 2.0 for Fine-grained Request Throttling" in the *API Gateway Best Practices*.
-  Error codes

   +------------+--------------------------------------------+------------------+--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Error Code | Error Message                              | HTTP Status Code | Description                                | Solution                                                                                                                                                                                 |
   +============+============================================+==================+============================================+==========================================================================================================================================================================================+
   | APIG.0308  | The throttling threshold has been reached. | 429              | The throttling threshold has been reached. | Try again after the throttling resumes. If the maximum number of requests sent to an API (accessible using a debugging domain name) per day is reached, bind an independent domain name. |
   +------------+--------------------------------------------+------------------+--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002076520562.png
