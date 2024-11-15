:original_name: apig_03_0046.html

.. _apig_03_0046:

Calling APIs
============

You can call APIs opened by others in APIG.

Usage Guidelines
----------------

-  An API can be accessed 1000 times by using the debugging domain name allocated when the API's group is created.
-  If the **CA** parameter is displayed in the **Create SSL Certificate** dialog box on the **API Management** > **API Policies** > **SSL Certificates** page of the APIG console, pay attention to the following restrictions when calling APIs:

   -  When calling an API with HTTP/1.0, do not use **Transfer-Encoding** in the request header.
   -  Do not use the CONNECT method.
   -  Do not use both **Content-Length** and **Transfer-Encoding** in the request header.
   -  Do not use spaces or control characters in the request line.
   -  Do not use spaces or control characters in the header name.
   -  Do not use spaces or control characters in the **Host** request header.
   -  Dot not use multiple **Host** parameters in the request header.

Prerequisites
-------------

Before calling an API, ensure that the network of your service system can communicate with the API access domain name or address.

-  If the service system and gateway are in the same VPC, the API can be directly accessed.
-  If the service system and gateway are in different VPCs of a region, connect them using a peering connection. For details, see section "VPC Peering Connection" in the *Virtual Private Cloud User Guide*.
-  If the service system and gateway are in different VPCs of different regions, create a cloud connection and load the two VPCs to connect them. For details, see section "Connecting VPCs in Different Regions" in the *Cloud Connect Getting Started*.
-  If the service system and gateway are connected over the public network, ensure that the gateway has been bound with an EIP.

.. _apig_03_0046__en-us_topic_0000001606053745_section3363103010129:

Obtaining API Calling Information
---------------------------------

Obtain API calling information from the API provider before you call an API.

-  Obtain API request information

   On the APIG console, choose **API Management** > **APIs**. On the **APIs** page, obtain the domain name, request method, and request path of the desired API. Click the API name to go to the **APIs** tab page, and obtain the basic information in the **Frontend Configuration** and **Backend Configuration** areas.

-  Obtain API authentication information

   Obtain the request authentication information according to the API's authentication mode.

   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Authentication Mode                 | Authentication Information                                                                                          |
   +=====================================+=====================================================================================================================+
   | App (signature)                     | Obtain the key and secret of a credential authorized for the API from the API provider, as well as the signing SDK. |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | App (simple authentication)         | Obtain the AppCode of a credential authorized for the API from the API provider.                                    |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | App (two-factor)                    | Obtain the information required for both app and custom authentication.                                             |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | App (app_secret)                    | Obtain the key and secret of a credential authorized for the API from the API provider.                             |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | App (app_basic)                     | Obtain the key and secret of a credential authorized for the API from the API provider.                             |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | IAM (token)                         | Obtain the username and password for the cloud platform.                                                            |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | IAM (AK/SK)                         | Obtain the AK/SK of an account for the cloud platform and the signing SDK.                                          |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | IAM (two-factor)                    | Obtain the information required for both IAM and custom authentication                                              |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Custom                              | Obtain the custom authentication information to carry in request parameters from the API provider.                  |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | None                                | No authentication information required.                                                                             |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Third-party authorizer (API policy) | Obtain third-party authorizer information to carry in request parameters from the API provider.                     |
   +-------------------------------------+---------------------------------------------------------------------------------------------------------------------+

   -  Credential key and secret

      On the APIG console, choose **API Management** > **Credentials**. Click the name of a credential authorized for the target API, and obtain the key and secret on the credential details page.

   -  Signing SDK

      On the APIG console, choose **Help Center** > **Using SDKs**, and download the SDK of the desired language.

   -  AppCode

      On the APIG console, choose **API Management** > **Credentials**. Click the name of a credential authorized for the target API, and obtain an AppCode in the **AppCodes** area of the credential details page.

.. _apig_03_0046__en-us_topic_0000001606053745_section19907427165210:

Calling an API
--------------

.. note::

   This section describes only the configuration of the request path and authentication parameters. For other parameters, such as timeout and SSL, configure them as required. To avoid service loss due to incorrect parameters, configure them by referring to the industry standards.

#. Construct an API request. Example:

   .. code-block:: text

      POST https://{Address}/{Path}?{Query}
      {Header}

      {
        {Body}
      }

   -  **POST**: request method. Replace it with the request method obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.
   -  *{Address}*: request address. Replace it with the domain name obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.

      +------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scenario                                                   | Request Parameter Configuration                                                                                                                                                                                                          |
      +============================================================+==========================================================================================================================================================================================================================================+
      | Calling an API with a domain name                          | Call an API using the debugging domain name allocated to the API group or a domain name bound to the group. No additional configuration is required.                                                                                     |
      +------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Calling an API in the **DEFAULT** group with an IP address | Call an API in the **DEFAULT** group with an IP address. No additional configuration is required.                                                                                                                                        |
      +------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Calling an API in a custom group with an IP address        | -  To use an IP address to call an API that uses app authentication in a non-DEFAULT group,                                                                                                                                              |
      |                                                            |                                                                                                                                                                                                                                          |
      |                                                            |    a. Set :ref:`configuration parameters <apig_03_0039>` **app_route** and **app_secret** of the gateway to **On**. After **app_route** is enabled, a credential cannot be authorized to APIs that use the same request path and method. |
      |                                                            |    b. Add header parameters **X-HW-ID** and **X-HW-APPKEY** and set them to the key and secret of a credential authorized for the API.                                                                                                   |
      |                                                            |                                                                                                                                                                                                                                          |
      |                                                            |    .. important::                                                                                                                                                                                                                        |
      |                                                            |                                                                                                                                                                                                                                          |
      |                                                            |       NOTICE:                                                                                                                                                                                                                            |
      |                                                            |       When calling an API through simple authentication (App authentication), you only need to add the header parameters **X-Apig-AppCode** and **host** to the request.                                                                 |
      |                                                            |                                                                                                                                                                                                                                          |
      |                                                            | -  To use an IP address to call an API that does not use app authentication in a non-DEFAULT group, add the header parameter **host**.                                                                                                   |
      +------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  *{Path}*: request path. Replace it with the request path obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.
   -  *{Query}*: (optional) query string in format "*Parameter_name*\ =\ *Parameter_value*", for example, **limit=10**. Separate multiple query strings with ampersands (&). For details, see the request parameters obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.
   -  *{Header}*: request header parameter in format "*Parameter_name*:*Parameter_value*", for example, **Content-Type:application/json**. For details, see the request parameters obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.
   -  *{Body}*: request body in JSON format. For details, see the request body description obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.

2. Add authentication information to the API request.

   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Authentication Mode                 | Request Parameter Configuration                                                                                                                                                                                                                                                                       |
   +=====================================+=======================================================================================================================================================================================================================================================================================================+
   | App (signature)                     | Use the obtained SDK to sign the API request. For details, see section "Calling APIs Through App Authentication" in the *API Gateway Developer Guide*.                                                                                                                                                |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App (simple authentication)         | Add the header parameter **X-Apig-AppCode** and set the parameter value to the AppCode obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`. For details, see :ref:`Getting Started <apig_03_1002>`.                                |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App (app_secret)                    | -  Set the **app_secret** parameter to **on** on the :ref:`Parameters <apig_03_0039>` tab of a gateway to enable app_secret authentication.                                                                                                                                                           |
   |                                     | -  Add the header parameter **X-HW-ID** and set the parameter value to the key obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.                                                                                                |
   |                                     | -  Add the header parameter **X-HW-AppKey** and set the parameter value to the secret obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`.                                                                                         |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App (app_basic)                     | -  To enable app_basic authentication, ensure that the **app_basic** parameter has been set to **on** on the :ref:`Parameters <apig_03_0039>` tab of the gateway.                                                                                                                                     |
   |                                     | -  Add the header parameter **Authorization** to the API request. The value is **"Basic "+base64(appkey+":"+appsecret)**. **appkey** and **appsecret** are the key and secret obtained in :ref:`Obtaining API Calling Information <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`. |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App (two-factor)                    | Add the information required for both app and custom authentication to the API request.                                                                                                                                                                                                               |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IAM (token)                         | Obtain a token from the cloud platform and add the header parameter **X-Auth-Token** with the token as the value. For details, see section "Token Authentication" in the *API Gateway Developer Guide*.                                                                                               |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IAM (AK/SK)                         | Use the obtained SDK to sign the API request. For details, see section "AK/SK Authentication" in the *API Gateway Developer Guide*.                                                                                                                                                                   |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IAM (two-factor)                    | Add the information for both IAM and custom authentication to the API request.                                                                                                                                                                                                                        |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Custom                              | Add the information required for custom authentication to the API request.                                                                                                                                                                                                                            |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | None                                | No authentication information required.                                                                                                                                                                                                                                                               |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Third-party authorizer (API policy) | Obtain third-party authorizer information to carry in request parameters from the API provider.                                                                                                                                                                                                       |
   +-------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
