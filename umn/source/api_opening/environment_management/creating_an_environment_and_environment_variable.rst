:original_name: apig-en-ug-180307037.html

.. _apig-en-ug-180307037:

Creating an Environment and Environment Variable
================================================

Scenario
--------

An API can be called in different environments, such as production, testing, and development environments. RELEASE is the default environment provided by APIG. You can define environment variables to allow an API to be called in different environments.

Environment variables are manageable and specific to environments. You can create variables in different environments to call different backend services using the same API.

For variables you define during API creation, you must create corresponding variables and values. For example, variable **Path** is defined for an API, and two variables with the same name are created and assigned values **/Stage/test** and **/Stage/AA** in environments 1 and 2, respectively. If the API is published and called in environment 1, the path **/Stage/test** is used. If the API is published and called in environment 2, the path **/Stage/AA** is used.


.. figure:: /_static/images/en-us_image_0000001142917658.png
   :alt: **Figure 1** Use of environment variables

   **Figure 1** Use of environment variables

.. note::

   You can create a maximum of 50 variables for an API group in each environment.

Prerequisites
-------------

You have :ref:`created an API group <apig-en-ug-180307015>`.

Creating an Environment
-----------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **Environments**.

#. Click **Create Environment**, and set the parameters listed in :ref:`Table 1 <apig-en-ug-180307037__en-us_topic_0114941621_en-us_topic_0080102731_table195413315428>`.

   .. _apig-en-ug-180307037__en-us_topic_0114941621_en-us_topic_0080102731_table195413315428:

   .. table:: **Table 1** Environment information

      =========== ===============================
      Parameter   Description
      =========== ===============================
      Name        Environment name.
      Description Description of the environment.
      =========== ===============================

#. Click **OK**.

   After the environment is created, it is displayed in the environment list.

Accessing an Environment
------------------------

You can call an API in the RELEASE environment by using a RESTful API. To access the API in other environments, add the **X-Stage** header to the request to specify an environment name. For example, add **X-Stage:DEVELOP** to the request header to access an API in the **DEVELOP** environment.

.. note::

   APIG does not support API debugging using environment variables.

Creating an Environment Variable
--------------------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **API Groups**.

#. Create a variable. You can use one of the following methods:

   -  Click the name of the target API group, and click the **Variables** tab on the displayed API group details page.
   -  In the **Operation** column of the target API group, choose **More** > **Manage Variable**.

#. Select an environment from the **Environment** drop-down list, and click **Create Variable**.

#. Set the parameters listed in :ref:`Table 2 <apig-en-ug-180307037__en-us_topic_0114941621_en-us_topic_0080102731_table179600199520>`.

   .. _apig-en-ug-180307037__en-us_topic_0114941621_en-us_topic_0080102731_table179600199520:

   .. table:: **Table 2** Parameters for creating an environment variable

      +-----------+----------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Description                                                                                                                |
      +===========+============================================================================================================================+
      | Name      | Name of the variable you want to create. Ensure that the name is the same as the name of the variable defined for the API. |
      +-----------+----------------------------------------------------------------------------------------------------------------------------+
      | Value     | The path to be used in the selected environment.                                                                           |
      +-----------+----------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

   .. note::

      If a variable is not needed, click **Delete** in the row containing the variable to delete it.

      Environment variable names and values will be displayed in plain text in API requests. Do not include sensitive information in the variable names and values.

Follow-Up Operations
--------------------

After creating an environment and variable, :ref:`publish APIs <apig-en-ug-180307023>` in the environment so that they can be called by API callers.
