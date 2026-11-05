:original_name: apig_03_0067.html

.. _apig_03_0067:

Importing APIs through an API Design File
=========================================

You can import Swagger and OpenAPI APIs to a new or existing API group on APIG. Before importing APIs, you need to understand the :ref:`APIG compatibility <apig_03_0083>` and supplement required :ref:`extended definitions <apig_03_0084>`.

You can also import APIs to APIG by referring to the following examples:

-  :ref:`Importing an HTTP Backend Service API <apig_03_0067__section199882525467>`
-  :ref:`Importing an HTTP VPC Backend Service API <apig_03_0067__section28931935154811>`
-  :ref:`Importing a Function Backend Service API <apig_03_0067__section8499101194913>`
-  :ref:`Importing a Mock Backend Service API <apig_03_0067__section1743417117504>`

Constraints
-----------

-  Constraints on APIG parameters:

   -  APIG does not support the configuration of request parameters in the **formData** and **body** locations.
   -  APIG does not support the configuration of parameters **consumes** and **produces**.
   -  The names of header parameters are case-insensitive.

-  Constraints on backend policies:

   -  When the backend type is **HTTP**, both HTTP and HTTP-VPC backends are supported.
   -  When the backend type is **HTTP-VPC**, both HTTP and HTTP-VPC backends are supported.
   -  When the backend type is **function**, only function backends are supported.
   -  When the backend type is **mock**, only mock backends are supported.

-  The API group and API :ref:`quotas <apig-pd-180307005__en-us_topic_0089881648_section10234165164214>` in API Gateway are sufficient.
-  If you use the **title** property in Swagger info and OpenAPI info to specify an API group name, the name of a new API group cannot be the same as that of an existing one.
-  If a conflict exists when you import APIs, the former API is imported successfully and the latter API cannot be imported. For example, if two APIs with the same name or request path exist in the imported API definition, a success message is displayed for the first imported API, and a failure message is displayed for the API to be imported subsequently.
-  If the definition of an API you are importing is the same as that of an existing API, you can overwrite the existing API or retain it. If you leave the existing API alone, the new API will not be imported.
-  If **Extended Definition Overwrite** is selected, the extended definition items (access control and request throttling policies) of an imported API will overwrite the existing extended definition items with the same name.
-  Imported APIs will not be automatically published in an environment. You can choose to publish them immediately or later.
-  The gRPC API, and the load balance channel, SSL certificate, and credential of an API cannot be imported.

Importing an API Design File
----------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. APIs can be imported in the following path:

   -  In the navigation pane, choose **API Management** > **API Groups**. Choose **Create API Group** > **Import API Design File**.
   -  Choose **API Management** > **APIs**. Click **Import APIs**.

4. Select an API file and click **Open**.
5. Set the parameters by referring to the following table.

   .. table:: **Table 1** Importing APIs

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                     |
      +===================================+=================================================================================================================================================================================================================================================================+
      | Import                            | Options:                                                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                 |
      |                                   | -  **New group**: Import APIs to a new API group. If you select this option, the system automatically creates an API group and imports the APIs into this group.                                                                                                |
      |                                   | -  **Existing group**: Import APIs to an existing API group. If you select this option, the system adds the APIs to the selected API group while retaining the existing APIs in the API group.                                                                  |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Group                         | Select an API group if **Import** is set to **Existing group**.                                                                                                                                                                                                 |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Basic Definition Overwrite        | You can select this option only when **Import** is set to **Existing group**. After this option is selected, an existing API will be overwritten if its name is the same as that of an imported API.                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Extended Definition Overwrite     | You can select this option only when **Import** is set to **New group**. If this option is selected, the extended definition items (access control and request throttling policies) of an imported API will overwrite the existing policies with the same name. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6. (Optional) To configure the APIs, click **Configure Global Settings**.

   a. Set the security configuration.

      Set the parameters by referring to the following table.

      .. table:: **Table 2** Security configuration

         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                 |
         +===================================+=============================================================================================================================================================================================================================================================================================================================================================================================+
         | Visibility                        | Determine whether the API is available to the public. Options:                                                                                                                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | -  **Public**: The API can be released to KooGallery.                                                                                                                                                                                                                                                                                                                                       |
         |                                   | -  **Private**: The API will be excluded when the API group to which it belongs is released on KooGallery.                                                                                                                                                                                                                                                                                  |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Authentication Mode               | The following authentication modes are available:                                                                                                                                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | -  **App**: Requests will be authenticated by APIG. App authentication is recommended.                                                                                                                                                                                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | -  **IAM**: Requests will be authenticated by IAM.                                                                                                                                                                                                                                                                                                                                          |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | -  **Custom**: Requests will be authenticated by using your own authentication system or service (for example, an OAuth-based authentication system).                                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | -  **None**: No authentication will be required. To call APIs that do not require authentication, construct standard HTTP requests and send them to APIG.                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   |    APIG **transparently transmits** requests to call an API that does not require authentication to the backend service. If you want requests to be authenticated on the API backend service, you can set **Security Authentication** to **None**. The API caller transfers the fields required for authentication to the backend service, and the backend service performs authentication. |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | API calling varies depending on the authentication mode. For details, see :ref:`Calling an Open API <apig_03_0046>`.                                                                                                                                                                                                                                                                        |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | .. caution::                                                                                                                                                                                                                                                                                                                                                                                |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   |    CAUTION:                                                                                                                                                                                                                                                                                                                                                                                 |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   |    -  If you set the authentication mode to **IAM** or **None**, any APIG user can access the API, which can result in excessive charges if the API is bombarded with malicious requests.                                                                                                                                                                                                   |
         |                                   |    -  If you set the authentication mode to **Custom**, you can create a function in FunctionGraph to interconnect with your own authentication system or service. Ensure that **FunctionGraph** is available in the current region.                                                                                                                                                        |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Simple Authentication             | This parameter is available only if you set **Security Authentication** to **App**.                                                                                                                                                                                                                                                                                                         |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | If you select app authentication, configure whether to enable simple authentication. In simple authentication, the **X-Apig-AppCode** parameter is added to the HTTP request header for quick authentication. APIG verifies only the AppCode and the request content does not need to be signed.                                                                                            |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | Simple authentication only supports HTTPS requests and does not support HTTP requests. For details, see :ref:`Configuring AppCodes for Simple Authentication <apig_03_0058>`.                                                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   |    After you enable simple authentication for an existing API, you need to publish the API again. For details, see :ref:`Publishing an API <apig_03_0014>`.                                                                                                                                                                                                                                 |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Two-Factor Authentication         | This parameter is available only if **Authentication Mode** is set to **App** or **IAM**.                                                                                                                                                                                                                                                                                                   |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | Determine whether to enable two-factor authentication for the API. If this option is enabled, API requests will be authenticated using a custom authorizer in addition to the app or IAM authentication you specify.                                                                                                                                                                        |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Custom Authorizer                 | This parameter is mandatory only if **Authentication Mode** is set to **Custom**.                                                                                                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | Select a custom authorizer you have created. If no custom authorizer is available, click **Create Custom Authorizer** on the right to create a frontend custom authorizer.                                                                                                                                                                                                                  |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | CORS                              | Determine whether to enable cross-origin resource sharing (CORS).                                                                                                                                                                                                                                                                                                                           |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | CORS allows browsers to send XMLHttpRequest to servers in other domains, overcoming the limitation that Asynchronous JavaScript and XML (AJAX) can be used only within the same domain.                                                                                                                                                                                                     |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | There are two types of CORS requests:                                                                                                                                                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | -  Simple requests: requests that have the **Origin** field in the header.                                                                                                                                                                                                                                                                                                                  |
         |                                   | -  Not-so-simple requests: HTTP requests sent before the actual request.                                                                                                                                                                                                                                                                                                                    |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                             |
         |                                   | If CORS (not-so-simple request) is enabled for an API, another API that uses the OPTIONS method must be created. For details, see :ref:`Enabling CORS <apig_03_0011>`.                                                                                                                                                                                                                      |
         +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Set the backend request configuration.

      Select an API backend service type and set parameters by referring to the following table.

      -  HTTP&HTTPS

         .. table:: **Table 3** Parameters for defining an HTTP&HTTPS backend service

            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter                         | Description                                                                                                                                                                                                                                                                                                            |
            +===================================+========================================================================================================================================================================================================================================================================================================================+
            | VPC Channel                       | Determine whether to use a load balance channel to access backend services.                                                                                                                                                                                                                                            |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | URL                               | A URL consists of a method, protocol, load balance channel/backend address, and path.                                                                                                                                                                                                                                  |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | -  **Method**                                                                                                                                                                                                                                                                                                          |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    Select **GET**, **POST**, **DELETE**, **PUT**, **PATCH**, **HEAD**, **OPTIONS**, or **ANY**. **ANY** indicates that all request methods are supported.                                                                                                                                                              |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | -  **Protocol**                                                                                                                                                                                                                                                                                                        |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    **HTTP** or **HTTPS**. **HTTPS** is recommended for transmitting important or sensitive data.                                                                                                                                                                                                                       |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    -  APIG supports WebSocket data transmission. HTTP is equivalent to WebSocket (ws), and HTTPS is equivalent to WebSocket Secure (wss).                                                                                                                                                                              |
            |                                   |    -  This protocol must be the one used by the backend service.                                                                                                                                                                                                                                                       |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | -  **Backend Address**                                                                                                                                                                                                                                                                                                 |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    **Set this parameter if no load balance channel is used.**                                                                                                                                                                                                                                                          |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    Enter the access address of the backend service in the format of *Host:Port*. *Host* indicates the IP address or domain name for accessing the backend service. *Port* is the port of the backend service. If no port is specified, port 80 is used for HTTP by default, and port 443 is used for HTTPS by default. |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    To use environment variables in the backend address, enclose the variables with number signs (#), for example, **#ipaddress#**. You can use multiple environment variables, for example, **#ipaddress##test#**.                                                                                                     |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    .. note::                                                                                                                                                                                                                                                                                                           |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |       If you have enabled public outbound access for a gateway, the IP address or domain name can be a public IP address (ECS EIP, public IP address of your own server, or ELB address), a public domain name, or a private network IP address. Private domain names cannot be used.                                  |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |       Gateways can transmit server name indication (SNI) to backend services during TLS handshake.                                                                                                                                                                                                                     |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | -  **Load Balance Channel**                                                                                                                                                                                                                                                                                            |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    **Set this parameter only if a load balance channel is used.** Select a load balance channel or :ref:`create one <apig_03_0040>`.                                                                                                                                                                                   |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    **To ensure a successful health check and service availability, configure the security groups of cloud servers in each channel to allow access from** **100.125.0.0/16.**                                                                                                                                           |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | -  **Path**                                                                                                                                                                                                                                                                                                            |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    The request path (URI) of the backend service. Ensure that any parameters in the path are enclosed in braces ({}). For example, **/getUserInfo/**\ *{userId}*.                                                                                                                                                      |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    If the path contains an environment variable, enclose the environment variable in number signs (#), for example, **/#path#**. You can use multiple environment variables, for example, **/#path##request#**.                                                                                                        |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | .. note::                                                                                                                                                                                                                                                                                                              |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    -  APIs whose URLs contain variables cannot be debugged on the API debugging page.                                                                                                                                                                                                                                  |
            |                                   |    -  For variables defined in URLs of APIs, corresponding environment variables and their values must be configured. Otherwise, the APIs cannot be published because there will be no values that can be assigned to the variables.                                                                                   |
            |                                   |    -  The variable name is case-sensitive.                                                                                                                                                                                                                                                                             |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Host Header                       | **This parameter is available only when the load balance channel is used.**                                                                                                                                                                                                                                            |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | Host header field in the backend service request. By default, the original host header in each request is used.                                                                                                                                                                                                        |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Timeout (ms)                      | Backend request timeout. Range: 1-60,000 ms.                                                                                                                                                                                                                                                                           |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | If a backend timeout error occurs during API debugging, increase the timeout to locate the reason.                                                                                                                                                                                                                     |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | .. note::                                                                                                                                                                                                                                                                                                              |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    If the current timeout does not meet your service requirements, modify the maximum timeout by referring to :ref:`Configuring Gateway Parameters <apig_03_0039>`. The value range is 1 ms to 600,000 ms. After modifying the maximum timeout, also modify the timeout here.                                          |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Retries                           | Number of attempts to retry requesting the backend service. Default: **0**; range: -1 to 10.                                                                                                                                                                                                                           |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | -  If the value is **-1**, the retry function is disabled. However, requests except for those using **POST** and **PATCH** will be retried once by default.                                                                                                                                                            |
            |                                   | -  If the value is within 0 to 10, the retry function is enabled, and requests will retry for the specified number of times. **0** indicates no retry attempts will be made.                                                                                                                                           |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | If a load balance channel is used, the number of retries must be less than the number of enabled backend servers in the channel.                                                                                                                                                                                       |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Two-Way Authentication            | **Set this parameter only when Protocol is set to HTTPS.**                                                                                                                                                                                                                                                             |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | Determine whether to enable two-way authentication between APIG and the backend service. If you enable this option, configure **backend_client_certificate** during :ref:`the configuration of gateway parameters <apig_03_0039>`.                                                                                     |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Backend Authentication            | Determine whether your backend service needs to authenticate API requests.                                                                                                                                                                                                                                             |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | If you enable this option, select a custom authorizer for backend authentication. :ref:`Custom authorizers <apig_03_0029>` are functions that are created in FunctionGraph to implement an authentication logic or to invoke an authentication service.                                                                |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   | .. note::                                                                                                                                                                                                                                                                                                              |
            |                                   |                                                                                                                                                                                                                                                                                                                        |
            |                                   |    Backend authentication relies on FunctionGraph and is only available in certain regions.                                                                                                                                                                                                                            |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      -  FunctionGraph

         FunctionGraph backends can be set only if FunctionGraph has been deployed in the current environment.

         .. table:: **Table 4** Parameters for defining a FunctionGraph backend service

            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter                         | Description                                                                                                                                                                                                                                                                                         |
            +===================================+=====================================================================================================================================================================================================================================================================================================+
            | Function Name                     | Automatically displayed when you select a function.                                                                                                                                                                                                                                                 |
            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Function URN                      | Identifier of the function.                                                                                                                                                                                                                                                                         |
            |                                   |                                                                                                                                                                                                                                                                                                     |
            |                                   | Click **Select** to specify a function.                                                                                                                                                                                                                                                             |
            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Version/Alias                     | Select a version or alias for your function. For details, see `Version Management <https://docs.otc.t-systems.com/en-us/usermanual/functiongraph/functiongraph_01_0180.html>`__ or `Alias Management <https://docs.otc.t-systems.com/en-us/usermanual/functiongraph/functiongraph_01_1829.html>`__. |
            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Invocation Mode                   | Select the invocation type of the function.                                                                                                                                                                                                                                                         |
            |                                   |                                                                                                                                                                                                                                                                                                     |
            |                                   | -  **Synchronous**: When receiving an invocation request, FunctionGraph immediately processes the request and returns a result. The client closes the connection once it has received a response from the backend.                                                                                  |
            |                                   | -  **Asynchronous**: The function invocation results of client requests do not matter to clients. When it receives a request, FunctionGraph queues the request, returns a response, and then processes requests one by one in idle state.                                                           |
            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Timeout (ms)                      | Backend request timeout. Range: 1-60,000 ms.                                                                                                                                                                                                                                                        |
            |                                   |                                                                                                                                                                                                                                                                                                     |
            |                                   | -  If a backend timeout error occurs during API debugging, increase the timeout to locate the reason.                                                                                                                                                                                               |
            |                                   | -  If the current timeout does not meet your service requirements, modify the maximum timeout by referring to :ref:`Configuring Gateway Parameters <apig_03_0039>`. The value range is 1 ms to 600,000 ms. After modifying the maximum timeout, also modify the timeout here.                       |
            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Backend Authentication            | Determine whether your backend service needs to authenticate API requests.                                                                                                                                                                                                                          |
            |                                   |                                                                                                                                                                                                                                                                                                     |
            |                                   | If you enable this option, select a custom authorizer for backend authentication. :ref:`Custom authorizers <apig_03_0029>` are functions that are created in FunctionGraph to implement an authentication logic or to invoke an authentication service.                                             |
            |                                   |                                                                                                                                                                                                                                                                                                     |
            |                                   | .. note::                                                                                                                                                                                                                                                                                           |
            |                                   |                                                                                                                                                                                                                                                                                                     |
            |                                   |    Backend authentication relies on FunctionGraph and is only available in certain regions.                                                                                                                                                                                                         |
            +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      -  Mock

         If the backend service is unavailable, use the Mock backend type to return the expected result to the API caller for debugging and verification.

         .. table:: **Table 5** Parameters for defining a Mock backend service

            +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Parameter                         | Description                                                                                                                                                                                                                                             |
            +===================================+=========================================================================================================================================================================================================================================================+
            | Status Code                       | Select the HTTP status code to be returned by the API.                                                                                                                                                                                                  |
            +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Response                          | You can use Mock for API development, debugging, and verification. It enables APIG to return a response without sending the request to the backend. This is useful if you need to test APIs when the backend is unavailable.                            |
            +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Backend Authentication            | Determine whether your backend service needs to authenticate API requests.                                                                                                                                                                              |
            |                                   |                                                                                                                                                                                                                                                         |
            |                                   | If you enable this option, select a custom authorizer for backend authentication. :ref:`Custom authorizers <apig_03_0029>` are functions that are created in FunctionGraph to implement an authentication logic or to invoke an authentication service. |
            |                                   |                                                                                                                                                                                                                                                         |
            |                                   | .. note::                                                                                                                                                                                                                                               |
            |                                   |                                                                                                                                                                                                                                                         |
            |                                   |    Backend authentication relies on FunctionGraph and is only available in certain regions.                                                                                                                                                             |
            +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Add Constant Parameter            | Customize the response header parameters for the API.                                                                                                                                                                                                   |
            |                                   |                                                                                                                                                                                                                                                         |
            |                                   | Click **Add Constant Parameter**, and enter the parameter name, value, and description.                                                                                                                                                                 |
            +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Click **Next**. You can view the configuration details in form, JSON, or YAML format.

   d. Confirm the configuration and click **Submit**.

7. In the displayed dialog box, determine whether to publish the APIs now.

   -  **Now**: Publish the APIs in a specified environment now.
   -  **Later**: Publish the APIs later. For details, see :ref:`Publishing an API <apig_03_0014>`.

8. Click **OK**. The **APIs** tab is displayed, showing the imported APIs.

.. _apig_03_0067__section199882525467:

Importing an HTTP Backend Service API
-------------------------------------

Import the request parameter definition of an HTTP backend service API that uses the GET method and is accessed through IAM authentication.

Swagger example:
----------------

.. code-block::

   swagger: "2.0"
   info:
     title: "importHttpEndpoint10"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/http/{userId}':
       get:
         operationId: "getUser3"
         description: "get user by userId"
         security:
         - apig-auth-iam: []
         schemes:
         - https
         parameters:
         - name: "test"
           description: "authorization token"
           type: "string"
           in: "header"
           required: true
         - name: "userId"
           description: "user id"
           type: "string"
           in: "path"
           required: true
         responses:
           "200":
             description: "user information"
         x-apigateway-request-type: "public"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "NORMAL"
         x-apigateway-backend:
           type: "HTTP"
           parameters:
           - name: "userId"
             value: "userId"
             in: "query"
             origin: "REQUEST"
             description: "user id"
           - name: "X-Invoke-User"
             value: "apigateway"
             in: "header"
             origin: "CONSTANT"
             description: "invoke user"
           httpEndpoints:
             address: "example.com"
             scheme: "http"
             method: "GET"
             path: "/users"
             timeout: 30000
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM

OpenAPI example:
----------------

.. code-block::

   openapi: 3.0.0
   info:
     title: importHttpEndpoint10
     version: '1.0'
   servers:
     - url: >-
         http://abc.com
     - url: >-
         https://abc.com
   paths:
     '/http/{userId}':
       get:
         description: get user by userId
         operationId: getUser3
         parameters:
           - description: authorization token
             example: ''
             in: header
             name: test
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
           - description: user id
             example: ''
             in: path
             name: userId
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         security:
           - apig-auth-iam: []
         servers:
           - url: >-
               https://abc.com
         x-apigateway-backend:
           httpEndpoints:
             address: example.com
             description: ''
             enableClientSsl: false
             method: GET
             path: /users
             retryCount: '-1'
             scheme: http
             timeout: 30000
           parameters:
             - description: invoke user
               in: HEADER
               name: X-Invoke-User
               origin: CONSTANT
               value: apigateway
             - description: user id
               in: QUERY
               name: userId
               origin: REQUEST
               value: userId
           type: HTTP
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: NORMAL
         x-apigateway-request-type: public
         x-apigateway-response: default
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses:
       default: {}

.. _apig_03_0067__section28931935154811:

Importing an HTTP VPC Backend Service API
-----------------------------------------

Import the request parameter definition of an HTTP VPC backend service API that uses the ANY method and is accessed through app authentication.


Swagger example:
----------------

.. code-block::

   swagger: "2.0"
   info:
     title: "importHttpVpcEndpoint"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/http-vpc':
       x-apigateway-any-method:
         operationId: "userOperation"
         description: "user operation resource"
         security:
         - apig-auth-app: []
         schemes:
         - https
         parameters:
         - name: "Authorization"
           description: "authorization signature"
           type: "string"
           in: "header"
           required: true
         responses:
           "default":
             description: "endpoint response"
         x-apigateway-request-type: "public"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "SWA"
         x-apigateway-backend:
           type: "HTTP-VPC"
           parameters:
           - name: "X-Invoke-User"
             value: "apigateway"
             in: "header"
             origin: "CONSTANT"
             description: "invoke user"
           httpVpcEndpoints:
             name: "userVpc"
             scheme: "http"
             method: "GET"
             path: "/users"
             timeout: 30000
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM


OpenAPI example:
----------------

.. code-block::

   openapi: 3.0.0
   info:
     description: import apis
     title: importHttpVpcEndpoint
     version: '1.0'
   servers:
     - url: >-
         http://abc.com
     - url: >-
         https://abc.com
   paths:
     /http-vpc:
       x-apigateway-any-method:
         description: user operation resource
         operationId: userOperation
         parameters:
           - description: authorization signature
             example: ''
             in: header
             name: Authorization
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         security:
           - apig-auth-app: []
         servers:
           - url: >-
               https://abc.com
         x-apigateway-backend:
           httpVpcEndpoints:
             cascade_flag: false
             description: ''
             enableClientSsl: false
             method: GET
             name: userVpc
             path: /users
             retryCount: '-1'
             scheme: http
             timeout: 30000
           parameters:
             - description: invoke user
               in: HEADER
               name: X-Invoke-User
               origin: CONSTANT
               value: apigateway
           type: HTTP-VPC
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: SWA
         x-apigateway-request-type: public
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses: {}

.. _apig_03_0067__section8499101194913:

Importing a Function Backend Service API
----------------------------------------

Import the request parameter definition of a FunctionGraph backend service API that uses the GET method and is accessed through IAM authentication.


Swagger example:
----------------

.. code-block::

   swagger: "2.0"
   info:
     title: "importFunctionEndpoint"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/function/{name}':
       get:
         operationId: "invokeFunction"
         description: "invoke function by name"
         security:
         - apig-auth-iam: []
         schemes:
         - https
         parameters:
         - name: "test"
           description: "authorization token"
           type: "string"
           in: "header"
           required: true
         - name: "name"
           description: "function name"
           type: "string"
           in: "path"
           required: true
         responses:
           "200":
             description: "function result"
         x-apigateway-request-type: "public"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "NORMAL"
         x-apigateway-backend:
           type: "FUNCTION"
           parameters:
           - name: "functionName"
             value: "name"
             in: "query"
             origin: "REQUEST"
             description: "function name"
           - name: "X-Invoke-User"
             value: "apigateway"
             in: "header"
             origin: "CONSTANT"
             description: "invoke user"
           functionEndpoints:
             function-urn: "your function urn address"
             version: "your function version"
             invocation-type: "async"
             timeout: 30000
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM


OpenAPI example:
----------------

.. code-block::

   openapi: 3.0.0
   info:
     description: import apis
     title: importHttpEndpoint
     version: '1.0'
   servers:
     - url: >-
         http://api.account.com
     - url: >-
         https://api.account.com
   paths:
     /function/{name}:
       get:
         description: invoke function by name
         operationId: invokeFunction
         parameters:
           - description: function name
             in: path
             name: name
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
             example: ''
           - description: authorization token
             in: header
             name: test
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
             example: ''
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         security:
           - apig-auth-iam: []
         servers:
           - url: >-
               https://api.account.com
         x-apigateway-backend:
           functionEndpoints:
             alias-urn: ''
             description: ''
             function-urn: "your function urn address"
             invocation-type: async
             network-type: V1
             timeout: 30000
             version: "your function version"
           parameters:
             - description: invoke user
               in: HEADER
               name: X-Invoke-User
               origin: CONSTANT
               value: apigateway
             - description: function name
               in: QUERY
               name: functionName
               origin: REQUEST
               value: name
           type: FUNCTION
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: NORMAL
         x-apigateway-request-type: public
         x-apigateway-response: default
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses:
       default: {}

.. _apig_03_0067__section1743417117504:

Importing a Mock Backend Service API
------------------------------------

Import the definition of a Mock backend service API that uses the GET method and is accessed without authentication.


Swagger example:
----------------

.. code-block::

   swagger: "2.0"
   info:
     title: "importMockEndpoint"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/mock':
       get:
         operationId: "mock"
         description: "mock test"
         schemes:
         - http
         responses:
           "200":
             description: "mock result"
         x-apigateway-request-type: "private"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "NORMAL"
         x-apigateway-backend:
           type: "MOCK"
           mockEndpoints:
             result-content: "{\"message\": \"mocked\"}"
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM


OpenAPI example:
----------------

.. code-block::

   openapi: 3.0.0
   info:
     description: import apis
     title: importHttpVpcEndpoint
     version: '1.0'
   servers:
     - url: >-
         http://abc.com
     - url: >-
         https://abc.com
   paths:
     /mock:
       get:
         description: mock test
         operationId: mock
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         servers:
           - url: >-
               http://abc.com
         x-apigateway-backend:
           mockEndpoints:
             description: ''
             result-content: '{"message": "mocked"}'
           type: MOCK
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: NORMAL
         x-apigateway-request-type: private
         x-apigateway-response: default
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses:
       default: {}

Related Documents
-----------------

-  After the API is imported and published, the API caller can :ref:`call the API <apig_03_0046>`. For the API that needs App authentication, perform the operations described in :ref:`(Optional) Configuring Authorization for API Calling <apig_03_0129>` before calling the API.
-  :ref:`What Are the Possible Causes of an API Import Failure? <apig-faq-2005024>`
-  :ref:`Is There a Template for Importing APIs Using a Swagger File? <apig-faq-2005025>`
