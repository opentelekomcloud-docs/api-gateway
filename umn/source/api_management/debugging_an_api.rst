:original_name: apig_03_0012.html

.. _apig_03_0012:

Debugging an API
================

After creating an API, debug it on the APIG console by setting HTTP headers and body to verify whether the API is running normally.

.. note::

   -  APIs with backend request paths containing variables cannot be debugged.
   -  If a **plug-in or traditional policy** is bound to an API, the policy does not take effect during API debugging.
   -  The maximum backend timeout is 60s for API debugging.

Prerequisites
-------------

You have set up the backend service of the API.

Procedure
---------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.

4. Click a group name.

5. On the **APIs** tab, select the target API and click **Debug**.

6. Configure the URL and request parameters of the API.

   Select a request method, protocol, and domain name, and set request parameters.

   Select the debugging or an independent domain name. If you select a wildcard domain name, specify the subdomain name.

   .. note::

      If the independent domain name you select is a wildcard domain name, you can use any of its subdomain names to access all APIs in the group to which the domain name is bound.

      For example, if a wildcard domain name is **\*.aaa.com**, the subdomain name can be **default.aaa.com** or **1.aaa.com**.

7. Click **Debug**.

8. The box on the lower right displays the response of the API request.

   -  If the debugging is successful, an HTTP status code starting with **2** and response details are displayed.
   -  If the request fails to be sent, an HTTP status code **4xx** or **5xx** is displayed. For details, see :ref:`Error Codes <apig_03_0048>`.

9. You can send more requests with different parameters and values to verify the API.

Follow-Up Operations
--------------------

After the API is successfully debugged, :ref:`publish <apig_03_0014>` the API in a specific environment so that the API can be called by users. To ensure security, :ref:`create policies <apig_03_0019>` for the API.
