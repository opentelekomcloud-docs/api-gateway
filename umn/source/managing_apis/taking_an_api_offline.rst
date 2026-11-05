:original_name: apig_03_0070.html

.. _apig_03_0070:

Taking an API Offline
=====================

You can remove APIs that you do not need from the environments where the APIs have been published.

.. caution::

   This operation will cause the APIs to be inaccessible in the environments. Ensure that you have notified users before this operation.

Prerequisites
-------------

-  You have created an API group and API.
-  You have published the API in an environment.


Taking an API Offline
---------------------

#. Go to the APIG console.

#. Select a dedicated gateway at the top of the navigation pane.

#. In the navigation pane, choose **API Management** > **API Groups**.

#. Click a group name to go to the **Group Information** page.

#. On the **APIs** page, take APIs offline.

   -  To take one API offline, select the API, and click **Take Offline** in the upper right.
   -  To take multiple APIs (<= 1000) offline, click **Batch**, select the APIs, and click the Take Offline icon.

#. Select the environment from which you want to take the API offline, and click **Yes**.

   After the API is taken offline, a red exclamation mark appears in the upper left corner of the **Publish Latest Version** button.

Related Documents
-----------------

-  After taking an API offline, delete it to release resources. **Deleting an API will permanently delete its configurations and historical records. Exercise caution when performing this operation.**
