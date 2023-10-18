:original_name: apig-en-ug-180307023.html

.. _apig-en-ug-180307023:

Publishing an API
=================

Scenario
--------

APIs can be called only after they have been published in an environment. You can publish APIs in different environments. APIG allows you to view the publication history (such as the version, description, time, and environment) of each API, and supports rollback of APIs to different historical versions.

.. note::

   -  If you modify a published API, you must publish it again for the modifications to take effect in the environment in which the API has been published.
   -  A maximum of 10 publication records of an API are retained in an environment.

Prerequisites
-------------

-  You have created an API group and API.
-  You have created an environment.


Publishing an API
-----------------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **APIs**.
#. Publish an API. You can use one of the following methods:

   -  Click **Publish** in the row containing the API you want to publish.
   -  Click the name of the target API, and click **Publish** in the upper right corner of the displayed API details page.

   .. note::

      To publish multiple APIs, select the APIs, and click **Publish**. You can publish a maximum of 1000 APIs at a time.

#. Select the environment where the API will be published, and enter a description.

   .. note::

      -  If the API has already been published in the environment, publishing it again will overwrite its definition in that environment.
      -  If there is no environment that meets your requirements, create a new one.

#. Click **Publish**.

Viewing Publication History
---------------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **APIs**.

#. Click the name of the target API.

#. Click the **Publication History** tab.

   The publication history of the API is displayed.

#. Click **View Details** in the **Operation** column of a version.

   The **View Details** dialog box displays the basic information, frontend and backend request information, input and constant parameters, parameter mappings, and example responses of the API.

#. To roll back the API to a historical version, click **Switch Version** in the row containing the target version, and click **Yes**.

   If "current version" is displayed next to the target version, the rollback was successful.

   When the API is called, configuration of the current version is used instead of the previously saved configuration.

   For example, an API was published in the RELEASE environment on August 1, 2018. On August 20, 2018, the API was published in the same environment after modification. If the version published on August 1 is set as the current version, configuration of this version will be used when the API is called.

FAQs About API Publishing
-------------------------

:ref:`Do I Need to Publish an API Again After Modification? <apig-en-faq-180307002>`

:ref:`Why Can't APIs Published in a Non-RELEASE Environment Be Accessed? <apig-en-faq-180606011>`

:ref:`Can I Invoke Different Backend Services by Publishing an API in Different Environments? <apig-en-faq-181016019>`
