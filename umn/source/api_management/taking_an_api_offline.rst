:original_name: apig_03_0070.html

.. _apig_03_0070:

Taking an API Offline
=====================

You can remove APIs that you do not need from the environments where the APIs have been published.

.. important::

   This operation will cause the APIs to be inaccessible in the environments. Ensure that you have notified users before this operation.

Prerequisites
-------------

-  You have created an API group and API.
-  You have published the API.

Procedure
---------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.
#. In the navigation pane, choose **API Management** > **API Groups**.
#. Click the name of the target API group.

   -  To take one API offline, select the API, and click **Take Offline** in the upper right.
   -  To take multiple APIs (<= 1000) offline, click **Batch**, select the APIs, and click the Take Offline icon.

#. Select the environment from which you want to take the API offline, and click **Yes**.

Follow-Up Operations
--------------------

After taking an API offline, delete it to release resources.
