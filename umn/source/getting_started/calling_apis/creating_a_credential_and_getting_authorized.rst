:original_name: apig-ug-180307010.html

.. _apig-ug-180307010:

Creating a Credential and Getting Authorized
============================================

.. _apig-ug-180307010__en-us_topic_0000001128537190_section101812113415:

Creating a Credential
---------------------

#. In the navigation pane, choose **API Management** > **Credentials**.
#. Click **Create Credential** and set credential information.

   .. table:: **Table 1** Credential information

      +-------------+------------------------------------------------------------------------------------------------------+
      | Parameter   | Description                                                                                          |
      +=============+======================================================================================================+
      | Name        | Credential name. It is recommended that you enter a name based on naming rules to facilitate search. |
      +-------------+------------------------------------------------------------------------------------------------------+
      | Description | Description about the credential.                                                                    |
      +-------------+------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Binding to an API
-----------------

#. In the **Operation** column of the :ref:`created credential <apig-ug-180307010__en-us_topic_0000001128537190_section101812113415>`, click **Bind to APIs**. **Note that only APIs that use app authentication can be bound.**
#. Select the environment, API group, and API created in :ref:`Opening APIs <apig-ug-180307001>`, and click **OK**.
