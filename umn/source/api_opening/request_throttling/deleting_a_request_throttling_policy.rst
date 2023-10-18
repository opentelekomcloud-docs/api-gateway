:original_name: apig-en-ug-180307032.html

.. _apig-en-ug-180307032:

Deleting a Request Throttling Policy
====================================

Scenario
--------

You can delete request throttling policies you no longer require.

Prerequisites
-------------

You have created a request throttling policy.

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **Request Throttling**.
#. Delete a request throttling policy. You can use one of the following methods:

   -  In the **Operation** column of the request throttling policy you want to delete, click **Delete**.
   -  Click the name of the target request throttling policy, and click **Delete** in the upper right corner of the displayed request throttling policy details page.

   .. note::

      -  If a request throttling policy has been bound to an API, unbind the policy and then delete it. To unbind a request throttling policy, go to the policy details page, click **Unbind** in the row that contains the API from which you want to unbind the policy, and click **Yes**.
      -  To delete multiple request throttling policies, select the policies, and click **Delete**. You can delete a maximum of 1000 request throttling policies at a time.

#. Click **Yes**.
