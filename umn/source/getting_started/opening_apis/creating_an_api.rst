:original_name: en-us_topic_0080101678.html

.. _en-us_topic_0080101678:

Creating an API
===============

Create an API with the following steps:

#. :ref:`Setting Basic Information <en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section8731554122615>`
#. :ref:`Defining API Request <en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section79773019167>`
#. :ref:`Defining Backend Service <en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section16484051169>`
#. :ref:`Defining Responses <en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section14735012301>`

.. _en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section8731554122615:

Setting Basic Information
-------------------------

#. In the navigation pane, choose **API Publishing** > **APIs**.
#. Click **Create API** and set the basic information.

   .. table:: **Table 1** Setting basic information

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                       |
      +===================================+===================================================================================================================================================================+
      | Name                              | API name. It is recommended that you enter a name based on naming rules to facilitate search.                                                                     |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Group                         | By default, the group created in :ref:`Creating an API Group <apig-en-ug-180307003>` is selected.                                                                 |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Gateway Response                  | Select a response to be displayed if APIG fails to process an API request.                                                                                        |
      |                                   |                                                                                                                                                                   |
      |                                   | The default gateway response is **default**.                                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Visibility                        | By default, **Public** is selected.                                                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Authentication           | API authentication mode. Set this parameter to **App**.                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Simple Authentication             | If you enable this option, APIG verifies only the AppCode and the request signature does not need to be verified. For this example, enable simple authentication. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Tag Name                          | Classification attribute used to quickly identify the API from other APIs.                                                                                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the API.                                                                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**.

.. _en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section79773019167:

Defining API Request
--------------------

#. On the **Define API Request** page, set the request information.

   .. table:: **Table 2** Parameters for defining API requests

      +-------------+------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Description                                                                                                            |
      +=============+========================================================================================================================+
      | Domain Name | The subdomain automatically allocated to the API group created in :ref:`Creating an API Group <apig-en-ug-180307003>`. |
      +-------------+------------------------------------------------------------------------------------------------------------------------+
      | Protocol    | Request protocol of the API. Set this parameter to **HTTPS**.                                                          |
      +-------------+------------------------------------------------------------------------------------------------------------------------+
      | Path        | The path for requesting the API.                                                                                       |
      +-------------+------------------------------------------------------------------------------------------------------------------------+
      | Matching    | By default, **Exact match** is selected.                                                                               |
      +-------------+------------------------------------------------------------------------------------------------------------------------+
      | Method      | Request method of the API. Set this parameter to **POST**.                                                             |
      +-------------+------------------------------------------------------------------------------------------------------------------------+
      | CORS        | For this example, disable this option.                                                                                 |
      +-------------+------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**.

.. _en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section16484051169:

Defining Backend Service
------------------------

#. On the **Define Backend Request** page, set the backend service information.
#. Select a backend service type. For this example, select **HTTP/HTTPS**.

   .. table:: **Table 3** Parameters for defining an HTTP/HTTPS backend service

      +-----------------+----------------------------------------------------------------------------------------------------------------+
      | Parameter       | Description                                                                                                    |
      +=================+================================================================================================================+
      | Protocol        | Set this parameter to **HTTP**.                                                                                |
      +-----------------+----------------------------------------------------------------------------------------------------------------+
      | Method          | Request method of the API. Set this parameter to **POST**.                                                     |
      +-----------------+----------------------------------------------------------------------------------------------------------------+
      | VPC Channel     | Determine whether the backend service will be accessed using a VPC channel. For this example, select **Skip**. |
      +-----------------+----------------------------------------------------------------------------------------------------------------+
      | Backend Address | Address of the backend service.                                                                                |
      +-----------------+----------------------------------------------------------------------------------------------------------------+
      | Path            | Path of the backend service.                                                                                   |
      +-----------------+----------------------------------------------------------------------------------------------------------------+
      | Timeout         | Backend service request timeout. Default value: 5000 ms.                                                       |
      +-----------------+----------------------------------------------------------------------------------------------------------------+

#. Click **Next**.

.. _en-us_topic_0080101678__en-us_topic_0080101678_en-us_topic_0165566289_en-us_topic_0080101678_section14735012301:

Defining Responses
------------------

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
