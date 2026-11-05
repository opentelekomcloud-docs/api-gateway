:original_name: apig_03_0069.html

.. _apig_03_0069:

Creating a Frontend Custom Authorizer
=====================================

To use your own API calling authentication system, create a custom authorizer.

Custom authorizers are classified into the following types:

-  Frontend: APIG uses a custom authentication function to authenticate API requests.
-  Backend: The backend service of an API uses a custom authentication function to authenticate requests forwarded by APIG.

This section describes how to create a frontend custom authorizer. Ensure that you have created a function backend before using it for a custom authorizer.


.. figure:: /_static/images/en-us_image_0000002076520542.png
   :alt: **Figure 1** Schematic diagram of frontend custom authentication

   **Figure 1** Schematic diagram of frontend custom authentication

The following figure shows the process of calling APIs through custom authentication.


.. figure:: /_static/images/en-us_image_0000002112004969.png
   :alt: **Figure 2** Calling APIs by using custom authentication

   **Figure 2** Calling APIs by using custom authentication

Constraints
-----------

FunctionGraph is required for custom authorizers. If FunctionGraph is unavailable in the selected region, custom authorizers are not supported.

.. _apig_03_0069__section79421723192017:

Creating a Function for Frontend Custom Authentication
------------------------------------------------------

You need to create a FunctionGraph function for frontend custom authentication and define the required authentication information in the function.

#. Log in to the FunctionGraph console.

#. In the navigation pane on the left, choose **Functions** > **Function List**.

#. Click **Create Function** and create a function based on the following table.

   .. table:: **Table 1** Configuring the function

      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter          | Description                                                                                                                                                 |
      +====================+=============================================================================================================================================================+
      | Create With        | Select **Create from scratch**.                                                                                                                             |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Function Type      | Type of the function. Default: **Event function**.                                                                                                          |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Region             | Select the same region as that of APIG.                                                                                                                     |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Function Name      | Set this name as planned. It is recommended that you enter a name based on naming rules to facilitate search.                                               |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project | Enterprise projects group and manage resources across regions. Resources in enterprise projects are logically isolated. **default** is selected by default. |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Agency             | An agency that delegates FunctionGraph to access other cloud services. For this example, select **Use no agency**.                                          |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Runtime            | **Python 2.7** is used as an example.                                                                                                                       |
      +--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Create Function**.

#. After the function is created, go to the function details page. On the **Code** tab page, set the function code.

   The function code must meet the following requirements:

   -  The function code has defined three types of request parameters in the following formats:

      -  Header parameters: event["headers"]["*Parameter name*"]
      -  Query string: **event["queryStringParameters"]["**\ *Parameter name*\ **"]**
      -  Custom user data: event["user_data"]

   -  The three types of request parameters obtained by the function are mapped to the custom authentication parameters defined in APIG.

      -  Header parameter: Corresponds to the identity source specified in **Header** for custom authentication. The parameter value is transferred when the API that uses custom authentication is called.
      -  Query string: Corresponds to the identity source specified in **Query** for custom authentication. The parameter value is transferred when the API that uses custom authentication is called.
      -  Custom user data: Corresponds to the user data for custom authentication. The parameter value is specified when the custom authorizer is created.

   -  The response of the function cannot be greater than 1 MB and must be displayed in the following format:

      .. code-block::

         {
             "statusCode":200,
             "body": "{\"status\": \"allow\", \"context\": {\"user\": \"abc\"}}"
         }

      The **body** field is a character string, which is JSON-decoded as follows:

      .. code-block::

         {
             "status": "allow/deny",
             "context": {
                 "user": "abc"
             }
         }

      -  The **statusCode** field is mandatory. If FunctionGraph is running properly and the code of the function complies with specifications, the value of statusCode is the response code of the function.

         -  If response code is not **200**, APIG considers that the function is abnormal and returns error code **500** and error information **Internal server error**.
         -  When the relaxed mode of the custom authorizer is turned on and the function fails to connect or returns **500** or **503**, the authorizer does not check the **status** field in the **body** field. Instead, it will immediately return a message indicating that the API was successfully invoked. The **context** field obtained from the function code will be empty.

      -  The **status** field is mandatory and is used to identify the authentication result. The authentication result can only be **allow** or **deny**. **allow** indicates that the authentication is successful, and **deny** indicates that the authentication fails.

      -  The **context** field is optional. It can be key-value pairs, but the key value cannot be a JSON object or an array.

         The **context** field contains custom user data. After successful authentication, the user data is mapped to the backend parameters. The parameter name in **context** is case-sensitive and must be the same as the system parameter name. The parameter name must start with a letter and can contain 1 to 32 characters, including letters, digits, hyphens (-), and underscores (_).

         After successful frontend authentication, the value **abc** of **user** in **context** is mapped to the **test** parameter in the **Header** location of backend requests.

   **Example header parameters:**

   .. code-block::

      # -*- coding:utf-8 -*-
      import json
      def handler(event, context):
          if event["headers"].get("test")=='abc':
              resp = {
                  'statusCode': 200,
                  'body': json.dumps({
                      "status":"allow",
                      "context":{
                          "user":"abcd"
                      }
                  })
              }
          else:
              resp = {
                  'statusCode': 200,
                  'body': json.dumps({
                      "status":"deny",
                  })
              }
          return json.dumps(resp)

   **Example query parameters:**

   .. code-block::

      # -*- coding:utf-8 -*-
      import json
      def handler(event, context):
          if event["queryStringParameters"].get("test")=='abc':
              resp = {
                  'statusCode': 200,
                  'body': json.dumps({
                      "status":"allow",
                      "context":{
                          "user":"abcd"
                      }
                  })
              }
          else:
              resp = {
                  'statusCode': 200,
                  'body': json.dumps({
                      "status":"deny",
                  })
              }
          return json.dumps(resp)

   **Example user data:**

   .. code-block::

      # -*- coding:utf-8 -*-
      import json
      def handler(event, context):
          if event.get("user_data")=='abc':
              resp = {
                  'statusCode': 200,
                  'body': json.dumps({
                      "status":"allow",
                      "context":{
                          "user":"abcd"
                      }
                  })
              }
          else:
              resp = {
                  'statusCode': 200,
                  'body': json.dumps({
                      "status":"deny",
                  })
              }
          return json.dumps(resp)

#. Test the function. In the **Configure Test Event** dialog box, select **apig-event-template**, edit the test event, and click **Save**. Then click **Test**.

   If the execution result is **Success**, the test is successful.

   Next, go to the APIG console to create a frontend custom authorizer. For details, see :ref:`Creating a Frontend Custom Authorizer <apig_03_0069__section72364219249>`

.. _apig_03_0069__section72364219249:


Creating a Frontend Custom Authorizer
-------------------------------------

Before creating a frontend custom authorizer, ensure that the function backend used for frontend custom authentication has been created. Otherwise, create a function backend first. For details, see :ref:`Creating a Function for Frontend Custom Authentication <apig_03_0069__section79421723192017>`.

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Custom Authorizers** page, click **Create Custom Authorizer**. Configure the custom authorizer parameters based on the following table.

   .. table:: **Table 2** Parameters for creating a custom authorizer

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================+
      | Name                              | Authorizer name. It can contain 3 to 64 characters and must start with a letter. Only letters, digits, and underscores (_) are allowed.                                                                                          |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Select **Frontend**.                                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Function URN                      | Select a function backend for frontend custom authentication. Only function backends in the **Deployed** state can be selected.                                                                                                  |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Version/Alias                     | Select a function version or alias. For details, see `FunctionGraph User Guide <https://docs.otc.t-systems.com/en-us/usermanual/functiongraph/functiongraph_01_0180.html>`__.                                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Cache Age (s)                | The time for caching authentication results.                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | The value ranges from 0s to 3,600s. **0** indicates that authentication results will not be cached.                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Relaxed Mode                      | -  When this option is enabled, APIG accepts client requests even when FunctionGraph cannot connect or returns an error code starting with "5". If there is a retry request, the last returned result is used.                   |
      |                                   | -  When this option is enabled, if a custom authorizer is used for backend authentication of an API, the value of the backend authentication parameter is empty.                                                                 |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | **The relaxed mode has security risks. Therefore, exercise caution when selecting this mode.**                                                                                                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Identity Sources                  | Request parameters used for authentication.                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | This parameter is mandatory when **Max. Cache Age (s)** is not **0**. When the cache is used, this parameter is used as a search criterion to query the authentication result.                                                   |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Send Request Body                 | Determine whether to send the body of each API request to the authentication function. If you enable this option, the request body will be sent to the authentication function in the same way as the headers and query strings. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User Data                         | Custom request parameters, which need to be used with **Identity Sources** when APIG invokes a function. Enter 1 to 2,048 characters.                                                                                            |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

5. Click **OK**.

   If the created custom authorizer is displayed in the custom authorizer list, the custom authorizer is created successfully.

Related Documents
-----------------

-  After a custom authorizer is created, you can create APIs with custom authentication. For details, see :ref:`Creating an API <apig_03_0010>`.
