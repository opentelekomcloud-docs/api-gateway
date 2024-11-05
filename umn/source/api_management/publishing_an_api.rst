:original_name: apig_03_0014.html

.. _apig_03_0014:

Publishing an API
=================

APIs can be called only after they have been published in an environment. You can publish APIs in different environments. APIG allows you to view the publication history (such as the version, description, time, and environment) of each API, and supports rollback of APIs to different historical versions.

.. note::

   -  If you modify a published API, you must publish it again for the modifications to take effect in the environment in which the API has been published.
   -  A maximum of 10 publication records of an API are retained in an environment.

Prerequisites
-------------

You have created an environment.


Publishing an API
-----------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.

4. Click a group name.

5. On the **APIs** tab, select the target API and click **Publish Latest Version**.

6. Select the environment where the API will be published, and enter a description.

   .. note::

      -  If the API has already been published in the environment, publishing it again will overwrite its definition in that environment.
      -  If there is no environment that meets your requirements, create a new one.

7. Click **OK**. After the API is published, the red exclamation mark (!) in the upper left corner of the **Publish Latest Version** button disappears.

   You can remove APIs from the environments where they have been published. This operation will cause the APIs to be inaccessible in the environments. Ensure that you have notified users before this operation. To remove an API, click **Take Offline**.

Viewing Publication History
---------------------------

#. On the **APIs** tab, select the target API.

#. Choose **More** > **View Publishing Records**.

#. Click **View Details** in the **Operation** column of a version.

   The **View Details** dialog box displays the basic information, frontend and backend request information, input and constant parameters, parameter mappings, and example responses of the API.

#. To roll back the API to a historical version, click **Switch Version** in the row containing the target version, and click **Yes**.

   If "current version" is displayed next to the target version, the rollback was successful.

   When the API is called, configuration of the current version is used instead of the previously saved configuration.

   For example, an API was published in the RELEASE environment on August 1, 2018. On August 20, 2018, the API was published in the same environment after modification. If the version published on August 1 is set as the current version, configuration of this version will be used when the API is called.

FAQs About API Publishing
-------------------------

:ref:`Do I Need to Publish an API Again After Modification? <apig-faq-180307002>`

:ref:`Can I Access an API Published in a Non-RELEASE Environment? <apig-faq-180606011>`

:ref:`Can I Invoke Different Backend Services by Publishing an API in Different Environments? <apig-faq-181016019>`
