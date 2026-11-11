:original_name: apig_03_0076.html

.. _apig_03_0076:

Cloning an API
==============

To improve API creation efficiency, you can clone an API with a custom name and path.

Constraints
-----------

Policies bound to an API cannot be cloned and can only be manually bound to the new API.

Prerequisites
-------------

You have created an API. If no API is available, create one by referring to :ref:`Creating a REST API <apig_03_0010>`.

Cloning APIs
------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Groups**.

4. Click a group name to go to the **Group Information** page.

5. On the **APIs** tab, choose **More** > **Clone**.

   Alternatively, choose **API Management** > **APIs**, locate the target API, and choose **More** > **Clone** in the same row.

6. Set the API name and path based on the following table.

   .. table:: **Table 1** Parameters for API cloning

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                    |
      +===================================+================================================================================================================================================================+
      | API Name                          | Enter an API name. It is recommended that you enter a name based on naming rules to facilitate search.                                                         |
      |                                   |                                                                                                                                                                |
      |                                   | Enter 3 to 255 characters, starting with a letter or digit. Use only letters, digits, and these special characters: -_./:()                                    |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Path                          | Request path of the API. Enclose parameters in braces. For example, **/a/{b}**. Or use a plus sign (+) to implement prefix matching. For example, **/a/{b+}**. |
      |                                   |                                                                                                                                                                |
      |                                   | **The path is case-sensitive.**                                                                                                                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   If the cloned API is displayed in the navigation tree on the left, the cloning is successful.

Related Documents
-----------------

After cloning an API, verify it by following the procedure in :ref:`Debugging an API <apig_03_0012>`.
