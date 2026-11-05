:original_name: apig_03_0130.html

.. _apig_03_0130:

Creating a Backend Custom Authorizer
====================================

To use your own API calling authentication system, create a custom authorizer.

-  Frontend: APIG uses a custom authentication function to authenticate API requests.
-  Backend: The backend service of an API uses a custom authentication function to authenticate requests forwarded by APIG.

This section describes how to create a backend custom authorizer. Ensure that you have created a function backend before using it for a custom authorizer.


.. figure:: /_static/images/en-us_image_0000002076520558.png
   :alt: **Figure 1** Schematic diagram of backend custom authentication

   **Figure 1** Schematic diagram of backend custom authentication

The following figure shows the process of calling APIs through custom authentication.


.. figure:: /_static/images/en-us_image_0000002112004973.png
   :alt: **Figure 2** Calling APIs through custom authentication

   **Figure 2** Calling APIs through custom authentication

Constraints
-----------

FunctionGraph is required for custom authorizers. If FunctionGraph is unavailable in the selected region, custom authorizers are not supported.

.. _apig_03_0130__section186156428353:

Creating a Function for Backend Custom Authentication
-----------------------------------------------------

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

#. After the function is created, go to the function details page.

   The function code must meet the following requirements:

   -  The custom user data contained in the function code must be in the following format: event["user_data"].

   -  The custom user data corresponds to the user data defined for the custom authorizer. You can define the user data in any format.

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

         The **context** field contains custom user data. After successful authentication, the user data is mapped to the backend parameters. The parameter name in **context** is case-sensitive and must be the same as the system parameter name. The parameter name in **context** must start with a letter and contain 1 to 32 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed.

         After successful backend authentication, the value **abc** of **user** in **context** is mapped to the **test** parameter in the **Header** location of backend requests and passed to the backend service.

   **Example user data:**

   .. code-block::

      # -*- coding:utf-8 -*-
      import json
      import base64
      def handler(event, context):
          exampleuserdata=base64.b64encode(event["user_data"])
          resp = {
              'statusCode': 200,
              'body': json.dumps({
                  "status":"allow",
                  "context":{
                      "user":exampleuserdata
                  }
              })
          }
          return json.dumps(resp)

#. Test the function. In the **Configure Test Event** dialog box, select **blank-template**, and set the following test event:

   .. code-block::

      {"user_data": "123"}

   Click **Save**. Then click **Test**.

   If the execution result is **Success**, the test is successful.

   Next, go to the APIG console to create a backend custom authorizer.


Creating a Backend Custom Authorizer
------------------------------------

Before creating a backend custom authorizer, ensure that the function backend used for backend custom authentication has been created. Otherwise, create a function first. For details, see :ref:`Creating a Function for Backend Custom Authentication <apig_03_0130__section186156428353>`.

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
      | Type                              | Select **Backend**.                                                                                                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Function URN                      | Select a function backend for custom authentication. Only function backends in the **Deployed** state can be selected.                                                                                                           |
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
      |                                   | This parameter is mandatory when **Type** is set to **Frontend** and **Max. Cache Age (s)** is not **0**. When the cache is used, this parameter is used as a search criterion to query the authentication result.               |
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
