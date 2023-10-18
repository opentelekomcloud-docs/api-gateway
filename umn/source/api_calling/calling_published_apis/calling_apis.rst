:original_name: apig-ug-0011.html

.. _apig-ug-0011:

Calling APIs
============

.. _apig-ug-0011__section15668112016810:

Obtaining APIs and Documentation
--------------------------------

Before calling APIs, obtain the request information from the API provider, including the access domain name, protocol, method, path, and request parameters.

Obtain APIs: from your company or from a partner

Obtain related documentation from the help center of the API provider's official website:

The authentication information to be obtained varies with the API authentication mode.

-  App authentication:

   -  Signature authentication: Obtain the key and secret (or client AppKey and AppSecret) of the app authorized for the API from the API provider as well as the SDK for calling the API.
   -  Simple authentication: Obtain the AppCode of the app authorized for the API from the API provider.
   -  Other authentication modes: Obtain the key and secret (or client AppKey and AppSecret) of the app authorized for the API from the API provider.

-  IAM authentication: The account credential (token or AK/SK obtained with the account and password) obtained on the cloud service platform is used for authentication. If the AK/SK is used for authentication, you also need to obtain the SDK from the API provider for calling the API.
-  Custom authentication: Obtain the custom authentication information to be carried in the request parameters from the API provider.
-  None: No authentication information is required.

.. _apig-ug-0011__section14411121782210:

Calling an API
--------------

.. note::

   This section describes only the configuration of the request path and authentication parameters. For other parameters, such as timeout and SSL, configure them as required. To avoid service loss due to incorrect parameters, configure them by referring to the industry standards.

#. Set the request path.

   +----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scenario                                                 | Request Parameter Configuration                                                                                                                                                                                                                                             |
   +==========================================================+=============================================================================================================================================================================================================================================================================+
   | Calling an API with a domain name                        | Call the API using :ref:`the subdomain name allocated to the API group or a domain name bound to the group <apig-en-ug-180327076>`. No additional configuration is required.                                                                                                |
   +----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Calling an API in the DEFAULT group with an IP address   | In the shared gateway, call an API in the DEFAULT group with an IP address. No additional configuration is required.                                                                                                                                                        |
   +----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Calling an API in a non-DEFAULT group with an IP address | -  To call APIs using an IP address, ensure that the **app_route** parameter has been set to **on** on the :ref:`Configuration Parameters <apig-ug-200801__en-us_topic_0272531149_section12828154014100>` tab page of the dedicated gateway.                                |
   |                                                          | -  To use an IP address to call an API that uses app authentication in a non-DEFAULT group, add the header parameters **X-HW-ID** and **X-HW-APPKEY** and set the parameter values to the key and secret of an app authorized for the API or a client AppKey and AppSecret. |
   |                                                          | -  To use an IP address to call an API that does not use app authentication in a non-DEFAULT group, add the header parameter **host**.                                                                                                                                      |
   +----------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Set the authentication parameters.

   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Authentication Mode                                | Request Parameter Configuration                                                                                                                                                                                                                                                                                      |
   +====================================================+======================================================================================================================================================================================================================================================================================================================+
   | App authentication (with a signature)              | Use the SDK to sign API requests. For details, see section "Calling APIs Through App Authentication" in the *API Gateway Developer Guide*.                                                                                                                                                                           |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App authentication (through simple authentication) | Add the header parameter **X-Apig-AppCode** and set the parameter value to the AppCode obtained in :ref:`Obtaining APIs and Documentation <apig-ug-0011__section15668112016810>`. For details, see :ref:`Getting Started <apig-ug-0012>`.                                                                            |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App authentication (with app_secret)               | -  On the :ref:`Configuration Parameters <apig-ug-200801__en-us_topic_0272531149_section12828154014100>` tab page of a dedicated gateway, the **app_secret** parameter has been set to **on** to enable app_secret authentication and **app_api_key** has been set to **off** to disable app_api_key authentication. |
   |                                                    | -  Add the header parameter **X-HW-ID** and set the parameter value to the key of the app authorized for the API or the client AppKey.                                                                                                                                                                               |
   |                                                    | -  Add the header parameter **X-HW-AppKey** and set the parameter value to the secret or AppSecret obtained in :ref:`Obtaining APIs and Documentation <apig-ug-0011__section15668112016810>`.                                                                                                                        |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | App authentication (with app_basic)                | -  To enable app_basic authentication, ensure that the **app_basic** parameter has been set to **on** on the :ref:`Configuration Parameters <apig-ug-200801__en-us_topic_0272531149_section12828154014100>` tab page of the dedicated gateway.                                                                       |
   |                                                    | -  Add the header parameter **Authorization** and set the parameter value to "Basic + base64 (*appkey* + : + *appsecret*)", in which *appkey* and *appsecret* are the key and secret (or AppKey and AppSecret) obtained in :ref:`Obtaining APIs and Documentation <apig-ug-0011__section15668112016810>`.            |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IAM authentication (with a token)                  | Obtain a token from the cloud platform and carry the token in API requests for authentication. For details, see section "Token Authentication" in the *API Gateway Developer Guide*.                                                                                                                                 |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | IAM authentication (with AK/SK)                    | Use an SDK to sign API requests. For details, see section "AK/SK Authentication" in the *API Gateway Developer Guide*.                                                                                                                                                                                               |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Custom authentication                              | Carry authentication information in API request parameters for authentication.                                                                                                                                                                                                                                       |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | None                                               | Call APIs without authentication.                                                                                                                                                                                                                                                                                    |
   +----------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
