:original_name: apig_03_0053.html

.. _apig_03_0053:

Querying Real-Time Traces
=========================

Scenarios
---------

After you enable CTS and the management tracker is created, CTS starts recording operations on cloud resources. CTS stores operation records generated in the last seven days.

This section describes how to query and export operation records of the last seven days on the CTS console.

-  :ref:`Viewing Real-Time Traces in the Trace List <apig_03_0053__en-us_topic_0179639644_section19271975203>`

.. _apig_03_0053__en-us_topic_0179639644_section19271975203:

Viewing Real-Time Traces in the Trace List
------------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Trace List** in the navigation pane on the left.

#. Set filters to search for your desired traces, as shown in :ref:`Figure 1 <apig_03_0053__en-us_topic_0179639644_fig139361441134311>`. The following filters are available:

   .. _apig_03_0053__en-us_topic_0179639644_fig139361441134311:

   .. figure:: /_static/images/en-us_image_0000001744598325.png
      :alt: **Figure 1** Filters

      **Figure 1** Filters

   -  **Trace Type**, **Trace Source**, **Resource Type**, and **Search By**: Select a filter from the drop-down list.

      -  If you select **Resource ID** for **Search By**, specify a resource ID.
      -  If you select **Trace name** for **Search By**, specify a trace name.
      -  If you select **Resource name** for **Search By**, specify a resource name.

   -  **Operator**: Select a user.
   -  **Trace Status**: Select **All trace statuses**, **Normal**, **Warning**, or **Incident**.
   -  Time range: You can query traces generated during any time range in the last seven days.
   -  Click **Export** to export all traces in the query result as a CSV file. The file can contain up to 5000 records.

#. Click **Query**.

#. On the **Trace List** page, you can also export and refresh the trace list.

   -  Click **Export** to export all traces in the query result as a CSV file. The file can contain up to 5000 records.
   -  Click |image2| to view the latest information about traces.

#. Click |image3| on the left of a trace to expand its details.

   |image4|

#. Click **View Trace** in the **Operation** column. The trace details are displayed.

   |image5|

#. For details about key fields in the trace structure, see section "Trace References" > "Trace Structure" and section "Trace References" > "Example Traces" in the *CTS User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001696838310.png
.. |image2| image:: /_static/images/en-us_image_0000001696678850.png
.. |image3| image:: /_static/images/en-us_image_0000001744678489.jpg
.. |image4| image:: /_static/images/en-us_image_0000001696838318.png
.. |image5| image:: /_static/images/en-us_image_0000001758618249.png
