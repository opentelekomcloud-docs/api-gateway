:original_name: apig_0080101678.html

.. _apig_0080101678:

Creating an API
===============

Procedure:

#. :ref:`Configuring Frontend Settings <apig_0080101678__en-us_topic_0000001174497011_en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section8731554122615>`
#. :ref:`Configuring Backend Settings <apig_0080101678__en-us_topic_0000001174497011_en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section16484051169>`

.. _apig_0080101678__en-us_topic_0000001174497011_en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section8731554122615:

Configuring Frontend Settings
-----------------------------

#. In the navigation pane, choose **API Management** > **APIs**.
#. Click **Create API** > **Create API** and configure the frontend.

   .. table:: **Table 1** Frontend definition

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                         |
      +===================================+=====================================================================================================================================+
      | Name                              | API name. It is recommended that you enter a name based on naming rules to facilitate search.                                       |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Group                             | By default, the group created in :ref:`Creating an API Group <apig-ug-180307003>` is selected.                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | URL                               | **Method**: Request method of the API. Set this parameter to **POST**.                                                              |
      |                                   |                                                                                                                                     |
      |                                   | **Protocol**: Set this parameter to **HTTPS**.                                                                                      |
      |                                   |                                                                                                                                     |
      |                                   | Subdomain name: The subdomain automatically allocated to the API group created in :ref:`Creating an API Group <apig-ug-180307003>`. |
      |                                   |                                                                                                                                     |
      |                                   | **Path**: Path for requesting the API.                                                                                              |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Gateway Response                  | Select a response to be displayed if API Gateway fails to process an API request.                                                   |
      |                                   |                                                                                                                                     |
      |                                   | The default gateway response is **default**.                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Matching                          | By default, **Exact match** is selected.                                                                                            |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Tags                              | Classification attribute used to quickly identify the API from other APIs.                                                          |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the API.                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------+

#. Configure security settings based on the following table.

   .. table:: **Table 2** API request definition

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                              |
      +=======================+==========================================================================================================================================================================+
      | Authentication Mode   | API authentication mode. Set this parameter to **App**.                                                                                                                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Simple Authentication | If you enable this option, API Gateway verifies only the AppCode and the request signature does not need to be verified. For this example, enable simple authentication. |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**.

.. _apig_0080101678__en-us_topic_0000001174497011_en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section16484051169:

Configuring Backend Settings
----------------------------

#. On the **Backend Configuration** page, set the backend service information.
#. Select a backend service type. For this example, select **HTTP&HTTPS**.

   .. table:: **Table 3** HTTP&HTTPS backend service definition

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                             |
      +===================================+=========================================================================================================================+
      | Load Balance Channel              | Determine whether the backend service will be accessed using a load balance channel. For this example, select **Skip**. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | URL                               | **Method**: Request method of the API. Set this parameter to **POST**.                                                  |
      |                                   |                                                                                                                         |
      |                                   | **Protocol**: Set this parameter to **HTTP**.                                                                           |
      |                                   |                                                                                                                         |
      |                                   | **Backend Address**: Address of the backend service.                                                                    |
      |                                   |                                                                                                                         |
      |                                   | **Path**: Path of the backend service.                                                                                  |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Timeout                           | Backend service request timeout. Default value: 5000 ms.                                                                |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------+

#. On the **Define Response** page, set the responses.

   .. table:: **Table 4** Defining responses

      +--------------------------+------------------------------------------------------------------------+
      | Parameter                | Description                                                            |
      +==========================+========================================================================+
      | Example Success Response | An example of a response returned when the API is called successfully. |
      +--------------------------+------------------------------------------------------------------------+
      | Example Failure Response | An example of a response returned when the API fails to be called.     |
      +--------------------------+------------------------------------------------------------------------+

#. Click **Finish**.
