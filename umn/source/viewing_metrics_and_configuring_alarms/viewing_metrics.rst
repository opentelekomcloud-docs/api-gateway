:original_name: apig_03_0034.html

.. _apig_03_0034:

Viewing Metrics
===============

Cloud Eye monitors the status of your APIs and allows you to view their metrics.

Viewing Metrics of an API
-------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Groups**.

4. Click a group name to go to the **Group Information** page.
5. In the left pane of the **APIs** tab, select an API.

6. View metrics of the API in the **Monitoring** area.

   View the call statistics of an API, including **Requests**, **Latency (ms)**, **Data Traffic (bytes)**, and **Errors**. You can also select a time range to view the data. The following time ranges are supported:

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
