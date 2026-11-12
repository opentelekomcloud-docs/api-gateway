:original_name: apig_03_0077.html

.. _apig_03_0077:

Third-Party Authorizer
======================

You can configure a third-party authorizer to connect your custom authentication service to API Gateway. Before calling a backend service, the gateway requests your authentication service for authentication. The gateway performs subsequent operations only after receiving a success response.

.. note::

   If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.

The following figure shows the principle of third-party authentication. After binding a third-party authentication policy to an API, call the API by referring to :ref:`Calling an Open API <apig_03_0046>`.

|image1|

Prerequisites
-------------

-  An API can be bound with only one third-party authorizer policy for a given environment, but each third-party authorizer policy can be bound to multiple APIs.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating a Third-Party Authorizer
---------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. In the **Select Policy Type** box, select **Third-Party Authorizer** in the **Plug-ins** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** Third-party authorizer parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================================================+
      | Name                              | Enter a policy name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Fixed value: **Third-Party Authorizer**.                                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the plug-in. Enter 1 to 255 characters.                                                                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Load Balance Channel              | Whether to connect a third-party authentication service using a load balance channel.                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Configure**: Select a :ref:`load balance channel <apig_03_0040>`.                                                                                                                                                                                                           |
      |                                   | -  **Skip**: Enter the path of the authentication service.                                                                                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Backend URL                       | -  **Method**                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    **GET**, **POST**, **PUT**, and **HEAD** are supported.                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Protocol**                                                                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    **HTTP** or **HTTPS**. **HTTPS** is recommended for transmitting important or sensitive data.                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Load Balance Channel** (optional)                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    **Set this parameter only if a load balance channel is used.** Select a load balance channel. If no required channel is available, click **Create Load Balance Channel** to create one.                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Backend Address** (optional)                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    **Set this parameter if no load balance channel is used.**                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    Enter the access address of the authentication service in the format of *Host:Port*. *Host* indicates the IP address or domain name for accessing the authentication service. If no port is specified, ports 80 and 443 are used by default for HTTP and HTTPS, respectively. |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    **Only IPv4 addresses are supported.**                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Path**                                                                                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    Path (URL) of the authentication service.                                                                                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Timeout (ms)                      | Timeout of the authentication service. It cannot exceed the max. timeout of the backend service. View the timeout limit on the **Parameters** tab of the gateway details page.                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Host Header                       | **Set this parameter only if a load balance channel is used.**                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | Host header field in the backend service request. By default, the original host header in each request is used.                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Brute Force Threshold             | IP addresses whose number of third-party authentication failure attempts within 5 minutes exceeds this threshold will be blocked. They will be unblocked after 5 minutes.                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | For example, if an IP address has failed third-party authentication more than the configured threshold in the third minute, the address is blocked, and will be unblocked after 2 minutes.                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Identity Sources                  | Parameters to obtain from the original API requests for third-party authentication. Max. 10 headers and 10 query strings. If not specified, all headers and query strings in the original requests will be used.                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Relaxed Mode                      | When this option is enabled, APIG accepts client requests even when your authentication service cannot connect or returns an error code starting with "5".                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allow Original Request Body       | When this option is enabled, the original request body is included for authentication.                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Request Body Size (bytes)         | Available only when **Allow Original Request Body** is enabled.                                                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | The value cannot exceed the max. request body size of the gateway. View the request body size limit on the **Parameters** tab of the gateway details page.                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allow Original Request Path       | When this option is enabled, the original request path is added to the end of the authentication request path.                                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Return Response                   | When this option is enabled, the authentication response is returned on failure.                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed Response Headers          | Headers to obtain from the authentication response and send to the backend service, when the authentication is successful.                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | Max. 10 headers.                                                                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Simple Authentication             | When this option is enabled, status codes starting with "2" indicate successful authentication.                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Authentication Result             | Available only when **Simple Authentication** is disabled.                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | Responses whose headers contain these parameters with the same values indicate successful authentication.                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Blacklist/Whitelist               | When this option is enabled, whether API requests require third-party authentication depends on the configured blacklist or whitelist rules.                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | -  Whitelist                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    API requests matching the whitelist rules do not require third-party authentication.                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  Blacklist                                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    API requests matching the blacklist rules require third-party authentication.                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameters                        | Define parameters for rule matching. **For security purposes, do not include sensitive information in these parameters.**                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Parameter Location**: the location of a parameter used for rule matching.                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   |    -  **path**: API request URI. This parameter is configured by default.                                                                                                                                                                                                        |
      |                                   |    -  **method**: API request method. This parameter is configured by default.                                                                                                                                                                                                   |
      |                                   |    -  **header**: the key of a request header.                                                                                                                                                                                                                                   |
      |                                   |    -  **query**: the key of a query string.                                                                                                                                                                                                                                      |
      |                                   |    -  **system**: a system parameter.                                                                                                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **Parameter**: the name of a parameter to match the specified value in a rule.                                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Conditions                        | Define conditions for rule matching.                                                                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | Click **Add Rule** and edit the rule name and conditions. In the **Condition Expressions** dialog box, select a parameter and operator, and enter a value. **For security purposes, do not include sensitive information in these parameters.**                                  |
      |                                   |                                                                                                                                                                                                                                                                                  |
      |                                   | -  **=**: equal to                                                                                                                                                                                                                                                               |
      |                                   | -  **!=**: not equal to                                                                                                                                                                                                                                                          |
      |                                   | -  **pattern**: regular expression                                                                                                                                                                                                                                               |
      |                                   | -  **enum**: enumerated values. Separate them with commas (,).                                                                                                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the policy is displayed in the policy list, the policy is created successfully.
   -  To clone this policy, click **Clone** in the **Operation** column. **The name of a cloned policy cannot be the same as that of any existing policy.**

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0077__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

Example Script
--------------

.. code-block::

   {
     "auth_request": {
       "method": "GET",
       "protocol": "HTTPS",
       "url_domain": "192.168.10.10",
       "timeout": 5000,
       "path": "/",
       "vpc_channel_enabled": false,
       "vpc_channel_info": null
     },
     "custom_forbid_limit": 100,
     "carry_body": {
       "enabled": true,
       "max_body_size": 1000
     },
     "auth_downgrade_enabled": true,
     "carry_path_enabled": true,
     "return_resp_body_enabled": false,
     "carry_resp_headers": [],
     "simple_auth_mode_enabled": true,
     "match_auth": null,
     "rule_enabled": false,
     "rule_type": "allow"
   }

.. _apig_03_0077__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.

.. |image1| image:: /_static/images/en-us_image_0000001560598294.png
