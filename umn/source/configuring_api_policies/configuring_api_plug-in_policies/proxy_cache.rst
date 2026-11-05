:original_name: apig_03_0111.html

.. _apig_03_0111:

Proxy Cache
===========

You can configure a proxy cache policy to cache responses returned by the backend service (server) in APIG. When a client sends the same request, APIG does not need to send the request to the backend service but directly returns the cached response. This effectively reduces the backend load and API invoking latency.

.. note::

   -  When the proxy cache policy is used, backend responses are cached to APIG. However, APIG now does not support cache data encryption, which poses security risks to sensitive data in responses. Therefore, exercise caution when configuring the policy.
   -  Policy parameters will be stored as plaintext. To prevent information leakage, do not contain sensitive information in these parameters.
   -  If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.

The following figure shows the principle of the response cache policy.

|image1|

Constraints
-----------

-  An API can be bound to only one response cache policy in an environment, but a response cache policy can be bound to multiple APIs.

-  The response cache policy supports only APIs that use the **GET**, **HEAD**, and **ANY** methods.

-  Response bodies larger than 1 MB will not be cached.

-  The cache for backend response is 128 MB.

-  APIG processes the cache according to the **Cache-Control** header in the backend response. If the backend does not return the **Cache-Control** header, the response is cached by default, and the **ttl** field configured in the policy is used as the cache expiration time.

-  By default, APIG does not process the **Cache-Control** header of the client. You can change this by configuring **client_cache_control** in the policy.

-  **Cache-Control** extended cache instructions are not part of the core HTTP cache standard document and are not supported.

   .. code-block::

      Cache-control: immutable
      Cache-control: stale-while-revalidate=<seconds>
      Cache-control: stale-if-error=<seconds>

-  APIG can cache only the **Content-Type**, **Content-Encoding**, and **Content-Language** headers. If you want to cache more headers, add them to the **Cached Backend Headers** in the policy. However, the system response headers (such as **x-apig-\*** and **x-request-id**) cannot be added.

-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.

-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.

-  Policies that have been bound to APIs cannot be deleted.

Creating a Proxy Cache Policy
-----------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **Proxy Cache** in the **Plug-ins** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** Proxy cache parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter a policy name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                              |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Fixed value: **Proxy Cache**.                                                                                                                                                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the proxy cache policy. Enter 1 to 255 characters.                                                                                                                                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                                                                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cache Proxy Key                   | The configuration is used to distinguish different caches.                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                              |
      |                                   | -  **system_params**: default gateway parameters. For details about the parameters, see :ref:`default gateway parameters <apig_03_0010__en-us_topic_0000001126143529_li672035111311>`.                                                                                                                       |
      |                                   | -  **parameters**: request query parameters.                                                                                                                                                                                                                                                                 |
      |                                   | -  **headers**: request headers.                                                                                                                                                                                                                                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HTTP Config                       | The HTTP **Status Code** and **Cache duration(s)** determine whether to cache data and how long the cache will be retained.                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                                              |
      |                                   | If HTTP parameters are not configured, the default **Status Code** is **200**. Range: 200-599. The default **Cache duration(s)** is **300**. Range: 1-720000.                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cache Proxy Modes                 | The gateway processes the cache through the **Cache-Control** request header in the client request. By default, the gateway rejects all client requests with the **Cache-Control** header.                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                              |
      |                                   | -  **all**: All client requests with the **Cache-Control** header are allowed.                                                                                                                                                                                                                               |
      |                                   | -  **off**: All client requests with the **Cache-Control** header are rejected.                                                                                                                                                                                                                              |
      |                                   | -  **apps**: Clients whose app IDs (credential IDs) are in the **datas** list are allowed.                                                                                                                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cached Backend Headers            | By default, only the **Content-Type**, **Content-Encoding**, and **Content-Language** headers can be cached. If you want to cache more headers, add them to the **Cached Backend Headers** in the policy. However, the system response headers (such as **x-apig-\*** and **x-request-id**) cannot be added. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the policy is displayed in the policy list, the policy is created successfully.
   -  To clone this policy, click **Clone** in the **Operation** column. **The name of a cloned policy cannot be the same as that of any existing policy.**

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0111__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

Example Script
--------------

.. code-block::

   {
     "cache_key": {
       "system_params": [
         "$context.sourceIp",
         "$context.requestId"
       ],
       "parameters": [
         "demo_parameters"
       ],
       "headers": [
         "demo_header"
       ]
     },
     "cache_http_status_and_ttl": [
       {
         "http_status": [
           200
         ],
         "ttl": 300
       }
     ],
     "client_cache_control": {
       "mode": "apps",
       "datas": [
         "demo_app_id_1,demo_app_id_2"
       ]
     },
     "cacheable_headers": [
       "demo_cacheable_headers_1,demo_cacheable_headers_2"
     ]
   }

.. _apig_03_0111__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.

.. |image1| image:: /_static/images/en-us_image_0000001890813809.png
