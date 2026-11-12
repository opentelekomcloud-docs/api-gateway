:original_name: apig_03_0034.html

.. _apig_03_0034:

Viewing Metrics
===============

When you need to learn about the running status of an API, troubleshoot calling exceptions, or evaluate API performance, you can view the monitoring metrics of API Gateway to obtain key data such as the number of requests, calling latency, data traffic, and errors. This helps you quickly locate problems and optimize API configurations. Cloud Eye monitors the status of your APIs and allows you to view their metrics.

Viewing Metrics of an API
-------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Groups**.

4. Click a group name to go to the **Group Information** page.
5. In the left pane of the **APIs** tab, select an API.

6. View metrics of the API in the **Monitoring** area.

   View the statistics of a called API, including **Requests**, **Latency**, **Data Traffic**, and **Errors**.

   -  **Requests**: total number of times an API is called in a statistical period.
   -  **Latency**: average time taken from the time an API request is received to the time a response is returned. Unit: milliseconds.
   -  **Data Traffic**: total volume of data transmitted in API requests and responses in a statistical period. Unit: KB.
   -  **Errors**: number and proportion of errors (4xx and 5xx) returned during API calls in a statistical period.

   You can also select the time range to view data. The following time ranges are supported:

   -  Data in the last hour is updated every 2 minutes.
   -  Data in the last 6 hours is updated every 2 hours.
   -  Data in the last day is updated every 2 hours.
   -  Data in the last week and last month is updated every day.

7. To view monitoring information about instances, click **More**.

   .. note::

      The monitoring data is retained for two days. To retain the data for a longer period, save it to an OBS bucket.

Viewing Metrics of an API group
-------------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **Monitoring & Analysis** > **API Monitoring**.

4. Select the target API group.

   You can view **Requests**, **Latency**, **Data Traffic**, and **Errors** of the APIs in the group in the last hour (data is updated every 2 minutes).

   -  **Requests**: total number of times an API is called in a statistical period.
   -  **Latency**: average time taken from the time an API request is received to the time a response is returned. Unit: milliseconds.
   -  **Data Traffic**: total volume of data transmitted in API requests and responses in a statistical period. Unit: KB.
   -  **Errors**: number and proportion of errors (4xx and 5xx) returned during API calls in a statistical period.

Related Documents
-----------------

-  If a metric is abnormal, you can configure alarm rules to receive notifications in a timely manner. For details, see :ref:`Configuring an Alarm Rule <apig_03_0033>`.
-  For details about the monitoring metrics supported by APIG, see :ref:`Monitoring Metrics <apig_03_0032>`.
-  For details about how to view API calls, see :ref:`Viewing API Call Logs <apig_03_0042>`.
