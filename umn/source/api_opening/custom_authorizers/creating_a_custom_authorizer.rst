:original_name: apic-ug-190430105.html

.. _apic-ug-190430105:

Creating a Custom Authorizer
============================

.. important::

   This feature is currently unavailable because FunctionGraph has not been launched.

Scenario
--------

APIG supports custom authentication of both frontend and backend requests.

-  Frontend custom authentication: If you already have an authentication system, you can configure it in a function and then create a custom authorizer by using the function to authenticate API requests.
-  Backend custom authentication: You can create a custom authorizer to authenticate requests for different backend services, eliminating the need to customize APIs for different authentication systems and simplifying API development. You only need to create a function-based custom authorizer in APIG to connect to the backend authentication system.

.. note::

   Custom authentication is implemented using FunctionGraph and not supported if FunctionGraph is unavailable in the selected region.

   For details about custom authentication, see *Developer Guide*.

The following figure shows the process of calling APIs through custom authentication.


.. figure:: /_static/images/en-us_image_0000001142758222.png
   :alt: **Figure 1** Calling APIs through custom authentication

   **Figure 1** Calling APIs through custom authentication

Prerequisites
-------------

-  You have created a function in FunctionGraph.
-  You have the **FunctionGraph Administrator** permission.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. Choose **API Publishing** > **Custom Authorizers**, and click **Create Custom Authorizer**.

#. Set the parameters listed in :ref:`Table 1 <apic-ug-190430105__table63864610016>`.

   .. _apic-ug-190430105__table63864610016:

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
      | Identity Sources                  | Request parameters for authentication. You can add headers and query strings. Header names are case-insensitive.                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | This parameter is mandatory only if you set **Type** to **Frontend**, and **Max. Cache Age (s)** is greater than **0**. When the cache is used, this parameter is used as a search criterion to query authentication results.    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Max. Cache Age (s)                | The time for caching authentication results.                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | Value **0** means that authentication results will not be cached. The maximum value is **3600**.                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Send Request Body                 | Determine whether to send the body of each API request to the authentication function. If you enable this option, the request body will be sent to the authentication function in the same way as the headers and query strings. |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   | .. note::                                                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                  |
      |                                   |    This option is available only for dedicated API gateways.                                                                                                                                                                     |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | User Data                         | Customized request parameters to be used together with **Identity Sources** when APIG invokes a function.                                                                                                                        |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.
