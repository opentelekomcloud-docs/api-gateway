:original_name: apig-en-ug-180307025.html

.. _apig-en-ug-180307025:

Debugging an API
================

Scenario
--------

After creating an API, debug it on the APIG console by setting HTTP headers and body parameters to verify whether the API is running normally.

.. note::

   -  APIs with backend request paths containing variables cannot be debugged.
   -  If an API has been bound with a request throttling policy, the policy will not work during debugging of the API.

Prerequisites
-------------

-  You have created an API group and API.
-  You have set up the backend service of the API.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **APIs**.

#. Debug an API. You can use one of the following methods:

   -  In the **Operation** column of the API you want to debug, choose **More** > **Debug**.
   -  Click the name of the target API, and click **Debug** in the upper right corner of the displayed API details page.

   On the left side, set the API request parameters listed in :ref:`Table 1 <apig-en-ug-180307025__en-us_topic_0080103327_table1699044810457>`. On the right side, view the API request and response information after you click **Send Request**.

   .. _apig-en-ug-180307025__en-us_topic_0080103327_table1699044810457:

   .. table:: **Table 1** Parameters for debugging an API

      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Parameter       | Description                                                                                               |
      +=================+===========================================================================================================+
      | Protocol        | This parameter can be modified only if you set **Protocol** to **HTTP&HTTPS** for the API.                |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Method          | This parameter can be modified only if you set **Method** to **ANY** for the API.                         |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Suffix          | You can define a path only if you have set **Matching** to **Prefix match** for the API.                  |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Path            | Request path of the API.                                                                                  |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Path Parameters | This parameter can be modified only if you have defined path parameters (such as **{test}**) for the API. |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Query Strings   | Query string parameters and values.                                                                       |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Headers         | HTTP headers and values.                                                                                  |
      +-----------------+-----------------------------------------------------------------------------------------------------------+
      | Body            | This parameter can be modified only if you set **Method** to **PATCH**, **POST**, or **PUT** for the API. |
      +-----------------+-----------------------------------------------------------------------------------------------------------+

   .. note::

      The fields displayed on the debugging page vary according to the request type.

#. After setting request parameters, click **Send Request**.

   The box on the lower right displays the response of the API request.

   -  If the debugging is successful, the HTTP status code **200** and response details are displayed.
   -  If the request fails to be sent, an HTTP status code **4xx** or **5xx** is displayed. For details, see :ref:`Error Codes <apig-en-ug-180530090>`.

#. You can send more requests with different parameters and values to verify the API.

   .. note::

      To modify the API configurations, click **Edit** in the upper right corner, and modify the parameters on the **Edit API** page.

Follow-Up Operations
--------------------

After the API is successfully debugged, :ref:`publish <apig-en-ug-180307023>` the API in a specific environment so that the API can be called by users. To ensure security of the API, create request throttling policies (see :ref:`Creating a Request Throttling Policy <apig-en-ug-180307029>`), access control policies (:ref:`Creating an Access Control Policy <apig-en-ug-180712097>`), and signature keys (:ref:`Creating and Using a Signature Key <apig-en-ug-180307041>`) for the API.
