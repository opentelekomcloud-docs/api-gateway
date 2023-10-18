:original_name: apig-lgug-200227001.html

.. _apig-lgug-200227001:

Adding an AppCode for Simple Authentication
===========================================

Scenario
--------

AppCodes are identity credentials of an app used to call APIs in simple authentication mode. In this mode, the **X-Apig-AppCode** parameter (whose value is an AppCode on the app details page) is added to the HTTP request header for quick response. APIG verifies only the AppCode and the request content does not need to be signed.

When an API is called using app authentication and simple authentication is enabled for the API, AppKey and AppSecret can be used to sign and verify the API request. AppCode can also be used for simple authentication.

.. note::

   -  For security purposes, simple authentication only supports API calls over HTTPS.
   -  You can create a maximum of five AppCodes for each app.

Prerequisites
-------------

You have created an app.

.. _apig-lgug-200227001__en-us_topic_0226991420_section216645314349:

Generating an AppCode
---------------------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Calling** > **Apps**.
#. Click the name of the target app.
#. Click the **AppCodes** tab.
#. Click **Add AppCode** to generate an AppCode. It can be automatically generated or customized.

Using AppCode for Simple Authentication of API Requests
-------------------------------------------------------

#. When creating an API, set **Security Authentication** to **App** and enable **Simple Authentication**.

   .. note::

      After you enable simple authentication for an existing API, you need to publish the API again to make the configuration take effect.

#. Bind an app to the API.

#. When sending a request, add the **X-Apig-AppCode** parameter to the request header and omit the request signature.

   For example, when using curl, add the **X-Apig-AppCode** parameter to the request header and set the parameter value to the :ref:`generated AppCode <apig-lgug-200227001__en-us_topic_0226991420_section216645314349>`.

   .. code-block::

      curl -X GET "https://api.exampledemo.com/testapi" -H "content-type: application/json"  -H "host: api.exampledemo.com" -H "X-Apig-AppCode: xhrJVJKABSOxc7d***********FZL4gSHEXkCMQC"
