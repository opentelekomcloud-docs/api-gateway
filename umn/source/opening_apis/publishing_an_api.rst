:original_name: apig_03_0014.html

.. _apig_03_0014:

Publishing an API
=================

APIs can be called only after they have been published in an environment. You can publish APIs in different environments. APIG allows you to view the publication history (such as the version, description, time, and environment) of each API, and supports rollback of APIs to different historical versions.

Constraints
-----------

-  If you modify a published API, you must publish it again for the modifications to take effect in the environment in which the API has been published.
-  A maximum of 10 publication records of an API are retained in an environment.


Publishing an API
-----------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.

4. Click a group name to go to the **Group Information** page.

5. On the **APIs** page, publish the API.

   -  Single publish: Select the API to be published and click **Publish Latest Version**.
   -  Batch publish: Click **Batch**, select the APIs to be published, and click the publish icon.

   You can also choose **API Management** > **APIs** to publish an API.

   -  Single publish: Click **Publish** in the row containing the API you want to publish.
   -  Batch publish: Select the APIs to be published and click **Publish** above the list.

6. Select the environment where the API will be published, and enter a description.

   -  If the API has already been published in the environment, publishing it again will overwrite its definition in that environment.
   -  If there is no environment that meets your requirements, create a new one.

7. Click **OK**. After the API is published, the red exclamation mark (!) in the upper left corner of the **Publish Latest Version** button disappears.

   You can remove APIs that you do not need from the environments where the APIs have been published. This operation will cause the API to be inaccessible in the specified environment. Ensure that you have notified users who use the API before taking it offline.

Viewing Publication History
---------------------------

#. On the **APIs** tab, select the target API.

#. Choose **More** > **View Publishing Records**.

#. Click **View Details** in the **Operation** column of a version.

   The **View Details** dialog box displays the basic information, frontend and backend request information, input and constant parameters, parameter mappings, and example responses of the API.

#. To roll back the API to a historical version, click **Switch to This Version** in the row containing the target version, and click **OK**.

   If "current version" is displayed next to the target version, the rollback was successful.

   When the API is called, configuration of the current version is used instead of the previously saved configuration.

   For example, an API was published in the RELEASE environment on August 1, 2018. On August 20, 2018, the API was published in the same environment after modification. If the version published on August 1 is set as the current version, configuration of this version will be used when the API is called.

Related Documents
-----------------

-  After the API is published, the API caller can :ref:`call the API <apig_03_0046>`. For the API that needs App authentication, perform the operations described in :ref:`(Optional) Configuring Authorization for API Calling <apig_03_0129>` before calling the API.
-  FAQs related to API publishing:

   -  :ref:`Do I Need to Publish an API Again After Modification? <apig-faq-180307002>`
   -  :ref:`Can I Access an API Published in a Non-RELEASE Environment? <apig-faq-180606011>`
   -  :ref:`Can I Invoke Different Backend Services by Publishing an API in Different Environments? <apig-faq-181016019>`
