:original_name: apig-ug-0004.html

.. _apig-ug-0004:

Creating a Plug-in
==================

APIG provides flexible extension capabilities for APIs through plug-ins.

.. important::

   Plug-in parameters will be stored as plaintext. To prevent information leakage, do not contain sensitive information in these parameters.

.. _apig-ug-0004__en-us_topic_0000001151883501_section126118109015:

Guidelines for Using Plug-ins
-----------------------------

-  An API can be bound with only one plug-in of the same type.
-  Plug-ins are independent of APIs. A plug-in takes effect for an API only after they are bound to each other. When binding a plug-in to an API, you must specify an environment where the API has been published. The plug-in takes effect for the API only in the specified environment.
-  After you bind a plug-in to an API, unbind the plug-in from the API, or update the plug-in, you do not need to publish the API again.
-  Taking an API offline does not affect the plug-ins bound to it. The plug-ins are still bound to the API if the API is published again.
-  Plug-ins that have been bound to APIs cannot be deleted.


Creating a Plug-in
------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **Plug-ins**.

#. Click **Create Plug-in**.

   In the **Create Plug-in** dialog box, configure the plug-in information.

   .. table:: **Table 1** Plug-in configuration

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                  |
      +===================================+==============================================================================================================================================================================+
      | Plug-in Name                      | Name of the plug-in you want to create. It is recommended that you enter a name based on certain naming rules to facilitate identification and search.                       |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Plug-in Type                      | Type of the plug-in, which determines the extension capabilities of the plug-in.                                                                                             |
      |                                   |                                                                                                                                                                              |
      |                                   | -  **CORS**: Specifies preflight request headers and response headers and automatically creates preflight request APIs for cross-origin API access.                          |
      |                                   | -  **HTTP Response Headers**: Enables you to customize HTTP response headers that will be displayed in an API response.                                                      |
      |                                   | -  **Request throttling**: Limits the number of times that an API can be called within a specific time period. Parameter-based, basic, and excluded throttling is supported. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Plug-in Content                   | Content of the plug-in, which can be configured in a form or using a script.                                                                                                 |
      |                                   |                                                                                                                                                                              |
      |                                   | The plug-in content varies depending on the plug-in type:                                                                                                                    |
      |                                   |                                                                                                                                                                              |
      |                                   | -  :ref:`CORS Plug-in <apig-ug-0002>`                                                                                                                                        |
      |                                   | -  :ref:`HTTP Response Header Management Plug-in <apig-ug-0005>`                                                                                                             |
      |                                   | -  :ref:`Request Throttling Plug-in <apig-ug-0015>`                                                                                                                          |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the plug-in.                                                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   After creating the plug-in, :ref:`bind it to the API <apig-ug-0004__en-us_topic_0000001151883501_section020918935713>` for which the plug-in will take effect.

.. _apig-ug-0004__en-us_topic_0000001151883501_section020918935713:

Binding a Plug-in to an API
---------------------------

#. In the navigation pane, choose **API Publishing** > **APIs**.
#. Click the name of the target API to go to the API details page.
#. On the **Plug-ins** tab page, click **Bind**.
#. In the **Bind Plug-in** dialog box, select an environment and plug-in type, and select the plug-in to bind.
#. Click **OK**.
