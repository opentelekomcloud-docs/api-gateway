:original_name: apig-en-ug-180307024.html

.. _apig-en-ug-180307024:

Taking an API Offline
=====================

Scenario
--------

You can remove APIs that you do not need from the environments where the APIs have been published.

.. important::

   This operation will cause the APIs to be inaccessible in the environments. Ensure that you have notified users before this operation.

Prerequisites
-------------

-  You have created an API group and API.
-  You have published the API.

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **APIs**.
#. Take the API offline. You can use one of the following methods:

   -  In the **Operation** column of the target API, choose **More** > **Take Offline**.
   -  Click the name of the target API, and click **Take Offline** in the upper right corner of the API details page.

   .. note::

      To take multiple APIs offline, select the APIs, and click **Take Offline**. You can take a maximum of 1000 APIs offline at a time.

#. Select the environment from which you want to take the API offline, and click **Yes**.

Follow-Up Operations
--------------------

After taking an API offline, delete it based on the instructions provided in :ref:`Deleting an API <apig-en-ug-180307027>`.
