:original_name: apig_03_0029.html

.. _apig_03_0029:

Custom Authorizers
==================

APIG supports custom authentication of both frontend and backend requests.

-  Frontend custom authentication: If you already have an authentication system, you can configure it in a function and then create a custom authorizer by using the function to authenticate API requests.
-  Backend custom authentication: You can create a custom authorizer to authenticate requests for different backend services, eliminating the need to customize APIs for different authentication systems and simplifying API development. You only need to create a function-based custom authorizer in APIG to connect to your backend authentication system.

.. note::

   **Custom authentication is implemented using FunctionGraph** and not supported if FunctionGraph is unavailable in the selected region.

   For details about custom authentication, see the relevant section in the *API Gateway Developer Guide*.

The following figure shows the process of calling APIs through custom authentication.


.. figure:: /_static/images/en-us_image_0000001176294490.png
   :alt: **Figure 1** Calling APIs through custom authentication

   **Figure 1** Calling APIs through custom authentication

Prerequisites
-------------

You have created a function in FunctionGraph.

Creating a Custom Authorizer
----------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. On the **Custom Authorizers** page, click **Create Custom Authorizer**.

   Configure custom authorizer parameters.

   .. table:: **Table 1** Parameters for creating a custom authorizer

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================+
      | Name                              | Authorizer name.                                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | -  **Frontend**: Authenticates access to APIs.                                                                                                                                                                                   |
      |                                   | -  **Backend**: Authenticates access to backend services.                                                                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Function URN                      | Select a FunctionGraph function.                                                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Version/Alias                     | Select a function version or alias. For details, see sections "Managing Versions" and "Managing Aliases" in the *FunctionGraph User Guide*.                                                                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Cache Age (s)                | The time for caching authentication results.                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | The value ranges from 0s to 3,600s. **0** indicates that authentication results will not be cached.                                                                                                                              |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Identity Sources                  | Request parameters used for authentication.                                                                                                                                                                                      |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | This parameter is mandatory only if you set **Type** to **Frontend**, and **Max. Cache Age (s)** is greater than **0**. When the cache is used, this parameter is used as a search criterion to query authentication results.    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Send Request Body                 | Determine whether to send the body of each API request to the authentication function. If you enable this option, the request body will be sent to the authentication function in the same way as the headers and query strings. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User Data                         | Customized request parameters to be used together with **Identity Sources** when APIG invokes a function.                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

5. Click **OK**.
