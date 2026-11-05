:original_name: apig_03_0112.html

.. _apig_03_0112:

Proxy Mirror
============

APIG mirrors source backend requests to images for traffic analysis and statistics without affecting online services.

.. note::

   If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.

Constraints
-----------

-  An API can be bound with only one proxy mirror policy for a given environment, but each proxy mirror policy can be bound to multiple APIs.
-  The response to the image request will be ignored.
-  The body size of an image request is defaulted to 12 MB and can be configured via the parameter :ref:`request_body_size <apig_03_0039>`. **A larger request body size indicates greater performance loss.** Exercise caution when performing this operation.
-  Not supported for APIs with a Mock backend.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating a Proxy Mirror Policy
------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **Proxy Mirror** in the **Plug-ins** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** Proxy mirror parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                            |
      +===================================+========================================================================================================================================================================================================================================================================================================================================+
      | Name                              | Enter a policy name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                                                                                                                        |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Fixed value: **Proxy Mirror**.                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the plug-in. Enter 1 to 255 characters.                                                                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                                                                                                                                                                           |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Protocol                          | The image request protocol. It must be the same as the user's image service protocol.                                                                                                                                                                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Image Address                     | Image service address, which consists of the IP address/domain name and port number. Max: 255 characters. Format: Host name:Port number. **Example: xxx.xxx.xxx:7443**. If the port number is not specified, the default HTTPS port **443** or the default HTTP port **80** is used.                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Request Path                      | This parameter is mandatory when **Protocol** is set to **HTTP** or **HTTPS**.                                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                                                                                                        |
      |                                   | Image request path. It can contain a maximum of 512 characters and must start with a slash (/) and comply with URI specifications. Special characters such as asterisks (``*``), percent signs (%), hyphens (-), underscores (_), and periods (.) are allowed. If not specified, the request path of the bound API is used by default. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Concatenation                     | Specifies how to concatenate the image request path.                                                                                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                                                                                                                        |
      |                                   | -  Replace: Uses the specified image request path.                                                                                                                                                                                                                                                                                     |
      |                                   | -  Prefix: Combines the specified image request path and the source request URI.                                                                                                                                                                                                                                                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Sampling Ratio                    | Sampling ratio of image requests. Range: 0.00001-1. Default: **1** (full sampling)                                                                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                                                                                                        |
      |                                   | For example, if there are 1,000 API requests and the sampling ratio is 0.1, 100 requests will be sampled.                                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Timeout (ms)                      | Image request timeout. Unit: ms. Default: 5,000 ms.                                                                                                                                                                                                                                                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mirror Request Body               | Mirrors the body of client requests. Enabled by default.                                                                                                                                                                                                                                                                               |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the policy is displayed in the policy list, the policy is created successfully.
   -  To clone this policy, click **Clone** in the **Operation** column. **The name of a cloned policy cannot be the same as that of any existing policy.**

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0112__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

Example Script
--------------

.. code-block::

   {
     "protocol": "HTTPS",
     "host": "X.X.X.X",
     "sample_ratio": 1,
     "timeout": 5000,
     "mirror_request_body_enabled": true,
     "path": "/ab",
     "path_concat_mode": "replace"
   }

.. _apig_03_0112__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.
