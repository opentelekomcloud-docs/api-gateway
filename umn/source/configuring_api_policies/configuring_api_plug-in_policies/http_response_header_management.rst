:original_name: apig_03_0022.html

.. _apig_03_0022:

HTTP Response Header Management
===============================

HTTP response headers are part of the response returned by APIG to a client that calls an API. They can be customized.

.. note::

   -  If this policy is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.
   -  Policy parameters will be stored as plaintext. To prevent information leakage, do not contain sensitive information in these parameters.

Constraints
-----------

-  An API can be bound to only one HTTP response header management policy for a given environment, but an HTTP response header management policy can be bound to multiple APIs.
-  You cannot modify the response headers (including **x-apig-\*** and **x-request-id**) added by APIG or the headers required for CORS.
-  Policies are independent of APIs. A policy takes effect for an API only after they are bound to each other. When binding a policy to an API, you must specify an environment where the API has been published. The policy takes effect for the API only in the specified environment.
-  Taking an API offline does not affect the policies bound to it. The policies are still bound to the API if the API is published again.
-  Policies that have been bound to APIs cannot be deleted.

Creating an HTTP Response Header Management Policy
--------------------------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Policies** tab, click **Create Policy**.

5. On the **Select Policy Type** page, select **HTTP Response Header Management** in the **Plug-ins** area.

6. Set the policy information based on the following table.

   .. table:: **Table 1** HTTP response header parameters

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================================================+
      | Name                              | Enter a policy name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                                                     |
      |                                   |                                                                                                                                                                                                              |
      |                                   | It can contain 3 to 255 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Fixed value: **HTTP Response Header Management**.                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description about the plug-in. Enter 1 to 255 characters.                                                                                                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Content                    | Content of the plug-in, which can be configured in a form or using a script.                                                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                              | Response header name, which is case-insensitive and must be unique within a policy. You can add a maximum of 10 response headers.                                                                            |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  Enter 1 to 32 characters (case-insensitive). Only letters, digits, periods (.), and hyphens (-) are allowed. The value must start with a letter.                                                          |
      |                                   | -  Do not start with **x-apig-** or **access-control-**, and do not use **x-request-id**, **Transfer-Encoding**, **Connection**, **Date**, or **server**.                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | System Parameters                 | Response header type.                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  **Custom Parameter**: Use a custom parameter as the value of the response header.                                                                                                                         |
      |                                   | -  **System Parameter**: Use a system parameter as the value of the response header.                                                                                                                         |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Value                             | Response header value. This parameter does not take effect and is left blank if you set **Action** to **Delete**. Enter 1 to 255 characters.                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Action                            | Response header operation. You can override, append, delete, skip, or add response headers.                                                                                                                  |
      |                                   |                                                                                                                                                                                                              |
      |                                   | **Override**                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  The value of this response header will override the value of the same response header that exists in an API response.                                                                                     |
      |                                   | -  If an API response contains multiple response headers with the same name, only the value of this response header will be returned.                                                                        |
      |                                   | -  If there is no response header with the same name in an API response, the value of this response header will be returned.                                                                                 |
      |                                   |                                                                                                                                                                                                              |
      |                                   | **Append**                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  If an API response contains the specified header, the value you set here will be added, following the existing value. The two values will be separated with commas (,).                                   |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  If an API response contains multiple response headers with the same name, values of these response headers will be returned and separated with commas (,), appended by the value of this response header. |
      |                                   | -  If there is no response header with the same name in an API response, the value of this response header will be returned.                                                                                 |
      |                                   |                                                                                                                                                                                                              |
      |                                   | **Delete**                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  This response header will be deleted if a response header with the same name exists in an API response.                                                                                                   |
      |                                   | -  If an API response contains multiple response headers with the same name, all these response headers will be deleted.                                                                                     |
      |                                   |                                                                                                                                                                                                              |
      |                                   | **Skip**                                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                              |
      |                                   | -  This response header will be skipped if a response header with the same name exists in an API response.                                                                                                   |
      |                                   | -  If an API response contains multiple response headers with the same name, values of all these response headers will be returned.                                                                          |
      |                                   | -  If there is no response header with the same name in an API response, the value of this response header will be returned.                                                                                 |
      |                                   |                                                                                                                                                                                                              |
      |                                   | **Add**                                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                              |
      |                                   | The value of this response header will be returned in an API response even if the response contains a response header with the same name.                                                                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  If the policy is displayed in the policy list, the policy is created successfully.
   -  To clone this policy, click **Clone** in the **Operation** column. **The name of a cloned policy cannot be the same as that of any existing policy.**

8. After the policy is created, perform the operations described in :ref:`Binding the Policy to APIs <apig_03_0022__section20100104416176>` to make the policy to take effect.

   **After you bind a policy to an API, unbind the policy from the API, or update the policy, your settings will take effect immediately, without the need to publish the API.**

Example Script
--------------

.. code-block::

   {
       "response_headers": [
           {
               "name": "test",
               "value": "test",
               "action": "append"
           },
           {
               "name": "test1",
               "value": "test1",
               "action": "override"
           }
       ]
   }

.. _apig_03_0022__section20100104416176:

Binding the Policy to APIs
--------------------------

#. Click the policy name to go to the policy details page.

#. Select an environment and click **Select APIs**.

#. Select the API group, environment, and required APIs.

   APIs can be filtered by API name or tag. The tag is defined during API creation.

#. Click **OK**.

   -  If an API no longer needs this policy, click **Unbind** in the row that contains the API.
   -  If there are multiple APIs that no longer need this policy, select these APIs, and click **Unbind** above the API list. You can unbind a policy from a maximum of 1000 APIs at a time.
