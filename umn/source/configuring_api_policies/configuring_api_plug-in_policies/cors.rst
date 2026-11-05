:original_name: apig_03_0021.html

.. _apig_03_0021:

CORS
====

For security purposes, the browser restricts cross-origin requests from being initiated from a page script. In this case, the page can access only the resources from the current domain. CORS allows the browser to send XMLHttpRequest to the server in a different domain. For details about CORS, see :ref:`CORS Calling of an Open API <apig_03_0011>`.

The CORS plug-in provides the capabilities of specifying preflight request headers and response headers and automatically creating preflight request APIs for cross-origin API access.

.. note::

   -  If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.
   -  Policy parameters will be stored as plaintext. To prevent information leakage, do not contain sensitive information in these parameters.

Constraints
-----------

-  An API can be bound to only one CORS policy for a given environment, but each CORS policy can be bound to multiple APIs.
-  APIs with the same request path in an API group can only be bound with the same CORS plug-in policy.
-  If you have enabled CORS for an API and have also bound the CORS plug-in to the API, the CORS plug-in will be used.
-  You cannot bind the CORS plug-in to APIs with the same request path as another API that uses the OPTIONS method.
-  When you bind a plug-in policy to an API (see :ref:`Binding the Policy to APIs <apig_03_0021__section20100104416176>`), ensure that the request method of the API is included in **allow_methods**.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.
-  If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.

Creating a CORS Policy
----------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **CORS** in the **Plug-ins** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** CORS parameters

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter a policy name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Fixed value: **CORS**.                                                                                                                                                                                                                                                                                                                                                                                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the CORS policy. Enter 1 to 255 characters.                                                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed Origins                   | **Access-Control-Allow-Origin** response header, which specifies either a single origin, which specifies the external domain URIs that are allowed to access the API. Separate multiple URIs using commas.                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | For requests that do not carry identity credentials, set this parameter to **\*** to allow access requests from all domains.                                                                                                                                                                                                                                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed Methods                   | **Access-Control-Allow-Methods** response header, which specifies the HTTP methods allowed when accessing the API. Separate multiple methods using commas.                                                                                                                                                                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allowed Headers                   | **Access-Control-Allow-Headers** response header, which specifies request headers that can be used when making an XMLHttpRequest. Separate multiple headers using commas.                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | By default, simple request headers **Accept**, **Accept-Language**, **Content-Language**, and **Content-Type** (only if the value is **application/x-www-form-urlencoded**, **multipart/form-data**, or **text/plain**) can be carried in requests. You do not need to configure these headers in this parameter.                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    -  When you create a CORS policy, **Allowed Headers** is blank by default, which means cross-origin requests cannot carry any custom headers.                                                                                                                                                                                                                                                                                         |
      |                                   |    -  Setting **Allowed Headers** to an asterisk (*) means cross-origin requests can carry any custom headers.                                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Exposed Headers                   | **Access-Control-Expose-Headers** response header, which specifies which response headers can be contained in the response of XMLHttpRequest. Separate multiple headers using commas.                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | By default, basic response headers **Cache-Control**, **Content-Language**, **Content-Type**, **Expires**, **Last-Modified**, and **Pragma** can be contained in the response. You do not need to configure these headers in this parameter.                                                                                                                                                                                             |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                                                                                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   |    -  When you create a CORS policy, **Exposed Headers** is blank by default, which means the JavaScript code of a browser cannot parse the headers in a cross-origin access response. However, the following basic response headers obtained using the getResponseHeader() method of the XMLHttpRequest object are excluded: **Cache-Control**, **Content-Language**, **Content-Type**, **Expires**, **Last-Modified**, and **Pragma**. |
      |                                   |    -  Setting **Exposed Headers** to an asterisk (*) means the JavaScript code of a browser can parse all the headers in a cross-origin access response.                                                                                                                                                                                                                                                                                 |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Maximum Age                       | **Access-Control-Max-Age** response header, which specifies for how many seconds the results of a preflight request can be cached. No more preflight requests will be sent within the specified period.                                                                                                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Allow Credentials                 | **Access-Control-Allow-Credentials** response header, which specifies whether XMLHttpRequest requests can carry cookies.                                                                                                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                          |
      |                                   | -  If the function is enabled, XMLHttpRequest requests can carry cookies.                                                                                                                                                                                                                                                                                                                                                                |
      |                                   | -  If the function is disabled, XMLHttpRequest requests cannot carry cookies.                                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the policy is displayed in the policy list, the policy is created successfully.
   -  To clone this policy, click **Clone** in the **Operation** column. **The name of a cloned policy cannot be the same as that of any existing policy.**

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0021__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

Example Script
--------------

.. code-block::

   {
     "allow_origin": "*",
     "allow_methods": "GET,POST,PUT",
     "allow_headers": "Content-Type,Accept,Accept-Ranges,Cache-Control",
     "expose_headers": "X-Request-Id,X-Apig-Latency",
     "max_age": 86400,
     "allow_credentials": true
   }

.. _apig_03_0021__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.
