:original_name: apig_03_0041.html

.. _apig_03_0041:

Managing Environments
=====================

An API can be called in different environments, such as production, testing, and development environments. RELEASE is the default environment provided by APIG.

Creating an Environment
-----------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.
4. Click the **Environments** tab.

5. Click **Create Environment** and set the environment information.

   .. table:: **Table 1** Environment information

      =========== ===============================
      Parameter   Description
      =========== ===============================
      Name        Environment name.
      Description Description of the environment.
      =========== ===============================

6. Click **OK**.

   After the environment is created, it is displayed in the environment list.

Accessing an Environment
------------------------

You can call an API in the RELEASE environment by using a RESTful API. To access the API in other environments, add the **X-Stage** header to the request to specify an environment name. For example, add **X-Stage:DEVELOP** to the request header to access an API in the **DEVELOP** environment.

.. note::

   APIG does not support API debugging with environment variables.

Follow-Up Operations
--------------------

After creating an environment, :ref:`publish APIs <apig_03_0014>` in the environment so that they can be called by API callers.
