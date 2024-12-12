:original_name: apig_03_0019.html

.. _apig_03_0019:

Creating a Policy and Binding It to APIs
========================================

APIG provides flexible API control policies.

.. important::

   Policy parameters will be stored as plaintext. To prevent information leakage, do not contain sensitive information in these parameters.

.. _apig_03_0019__en-us_topic_0000001221774151_en-us_topic_0000001151883501_section126118109015:

Guidelines
----------

-  An API can be bound with only one policy of the same type.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  After you bind a policy to an API, unbind the policy from the API, or update the policy, you do not need to publish the API again.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating a Policy
-----------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.
4. On the **Policies** tab, click **Create Policy**.
5. Click the desired policy type.

   -  **Plug-in policies**

      Set the policy information.

      .. table:: **Table 1** Policy configuration

         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                        |
         +===================================+====================================================================================================================================================================================+
         | Name                              | Enter a policy name that conforms to specific rules to facilitate search.                                                                                                          |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Type                              | Type of the policy, which determines the extension capabilities.                                                                                                                   |
         |                                   |                                                                                                                                                                                    |
         |                                   | .. note::                                                                                                                                                                          |
         |                                   |                                                                                                                                                                                    |
         |                                   |    If a policy type is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.                                                      |
         |                                   |                                                                                                                                                                                    |
         |                                   | -  **CORS**: Provides the capabilities of specifying preflight request headers and response headers and automatically creating preflight request APIs for cross-origin API access. |
         |                                   | -  **HTTP Response Header Management**: Enables you to customize HTTP response headers that will be displayed in an API response.                                                  |
         |                                   | -  **Request Throttling 2.0**: Limits the number of times that an API can be called within a specific time period. Parameter-based, basic, and excluded throttling is supported.   |
         |                                   | -  **Kafka Log Push**: Pushes API calling logs to Kafka so that you can view these logs.                                                                                           |
         |                                   | -  **Circuit Breaker**: Protects your backend service when a performance issue occurs.                                                                                             |
         |                                   | -  **Third-Party Authorizer**: Authenticates API requests with your own service.                                                                                                   |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Description about the plug-in.                                                                                                                                                     |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                       |
         |                                   |                                                                                                                                                                                    |
         |                                   | The plug-in content varies depending on the plug-in type:                                                                                                                          |
         |                                   |                                                                                                                                                                                    |
         |                                   | -  :ref:`CORS <apig_03_0021>`                                                                                                                                                      |
         |                                   | -  :ref:`HTTP Response Header Management <apig_03_0022>`                                                                                                                           |
         |                                   | -  :ref:`Request Throttling 2.0 <apig_03_0054>`                                                                                                                                    |
         |                                   | -  :ref:`Kafka Log Push <apig_03_0061>`                                                                                                                                            |
         |                                   | -  :ref:`Circuit Breaker <apig_03_0023>`                                                                                                                                           |
         |                                   | -  :ref:`Third-Party Authorizer <apig_03_0077>`                                                                                                                                    |
         +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  **Traditional policies**

      The policy content varies depending on the policy type:

      -  :ref:`Request Throttling <apig_03_0025>`
      -  :ref:`Access Control <apig_03_0027>`
      -  :ref:`Signature Keys <apig_03_0028>`

6. Click **OK**.

   -  To clone this policy, click **Clone** in the **Operation** column.

      .. note::

         -  The name of a cloned policy cannot be the same as that of any existing policy.
         -  **Request throttling** and **signature key** policies cannot be cloned.

   -  After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0019__en-us_topic_0000001221774151_en-us_topic_0000001151883501_section020918935713>` for the policy to take effect for the API.

.. _apig_03_0019__en-us_topic_0000001221774151_en-us_topic_0000001151883501_section020918935713:

Binding the Policy to APIs
--------------------------

#. Click a policy name to go to the policy details page.
#. In the **APIs** area, select an environment and click **Select APIs**.
#. Select the API group, environment, and required APIs.
#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.
