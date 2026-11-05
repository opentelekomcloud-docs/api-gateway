:original_name: apig_03_0007.html

.. _apig_03_0007:

(Optional) Configuring the Environment and Environment Variables
================================================================

An environment refers to the usage scope of an API. An API can be called only after it is published in an environment. APIs can be published in different customized environments, such as the development environment and test environment. RELEASE is the default and formal publishing environment of the system.

Environment variables are specific to environments. If environment variables are defined in backend information of an API, you need to add the variables to the environment. You can create variables in different environments to call different backend services using the same API.

Example: an API whose variable **Path** is defined in the backend request path. If variable **Path** is configured for environment 1 and is assigned value **/Stage/test**, use the backend request path **/Stage/test** to call this API in this environment. If variable **Path** is configured for environment 2 and is assigned value **/Stage/AA**, use the backend request path **/Stage/AA** to call this API in this environment.


.. figure:: /_static/images/en-us_image_0000001178542512.png
   :alt: **Figure 1** Use of environment variables

   **Figure 1** Use of environment variables

Creating an Environment
-----------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.
4. Click the **Environments** tab.

5. Click **Create Environment** and configure basic information based on the following table.

   .. table:: **Table 1** Environment information

      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Description                                                                                                                                |
      +=============+============================================================================================================================================+
      | Name        | Environment name. The name contains 3 to 64 characters. It can contain letters, digits, and underscores (_), and must start with a letter. |
      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------+
      | Description | Description of the environment. Enter 1 to 255 characters.                                                                                 |
      +-------------+--------------------------------------------------------------------------------------------------------------------------------------------+

6. Click **OK**.

   -  After the environment is created, it is displayed in the environment list.

   -  To delete an environment, click **Delete** in the **Operation** column.

      The **RELEASE** environment cannot be deleted. If there are published APIs in the environment, you need to bring them offline before deleting the environment. Deleted environments cannot be recovered.

   -  When a user needs to call an open API, the API in the **RELEASE** environment is called by default. To access an API in another environment, add the **X-Stage** parameter (whose value is an environment name) to the header of the API request. For example, to access an API in the **Develop** environment, add **X-Stage: Develop** to the header of the API request.

Creating an Environment Variable
--------------------------------

#. Go to the APIG console.

2. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.
4. Click a group name to go to the **Group Information** page.
5. In the **Environment Variables** area, select an environment. If no environment is available, click **Create Environment** to create one.
6. Click **Add Environment Variable** and enter the variable information based on the following table.

   -  Environment variable names and values will be displayed in plain text in API requests. Do not include sensitive information in the variable names and values.
   -  APIG does not support API debugging with environment variables.

   .. table:: **Table 2** Adding an environment variable

      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================================================================================================================================+
      | Name                              | Variable name. Ensure that the name is the same as the name of the variable defined for the API. The variable name is equivalent to **#Name#** in an API definition. Characters between the number signs are case-sensitive. The variable name will be replaced with the variable value after API publication. |
      |                                   |                                                                                                                                                                                                                                                                                                                |
      |                                   | The variable name contains 3 to 32 characters. It can contain letters, digits, underscores (_), and hyphens (-), and must start with a letter.                                                                                                                                                                 |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Value                             | Use letters, digits, underscores (_), hyphens (-), slashes (/), periods (.), and colons (:). (Max. 255 characters)                                                                                                                                                                                             |
      +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

7. Click **OK**.

   -  After the environment variable is created, it is displayed in the environment variable list.
   -  To delete an environment variable, click **Delete** in the **Operation** column. Deleted environment variables cannot be recovered.
   -  If an environment variable is modified, you need to publish the API again. Otherwise, the new variable does not take effect.

Related Documents
-----------------

-  You can :ref:`publish an API in the environment <apig_03_0014>` for calling.
