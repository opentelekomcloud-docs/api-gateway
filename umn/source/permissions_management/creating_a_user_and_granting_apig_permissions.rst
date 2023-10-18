:original_name: apig-ug-190529109.html

.. _apig-ug-190529109:

Creating a User and Granting APIG Permissions
=============================================

This topic describes how to use Identity and Access Management (IAM) to implement permissions control for your APIG resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing APIG resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or a cloud service to perform O&M on your APIG resources.

If your account does not require individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <apig-ug-190529109__en-us_topic_0172480077_en-us_topic_0170877287_fig15451536531>`).

Prerequisites
-------------

Learn about the permissions (see :ref:`Table 1 <apig-ug-190529109__en-us_topic_0172480077_table13382143731910>`) supported by APIG and choose policies or roles according to your requirements. For the permissions of other services, see **Others** > **Permissions** in the service list.

.. _apig-ug-190529109__en-us_topic_0172480077_table13382143731910:

.. table:: **Table 1** System-defined roles and policies supported by APIG

   +---------------------+-------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | Role/Policy Name    | Description                                                                                                 | Type                  | Dependency |
   +=====================+=============================================================================================================+=======================+============+
   | APIG Administrator  | Administrator permissions for APIG. Users granted these permissions can use all functions of API gateways.  | System-defined role   | None       |
   +---------------------+-------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | APIG FullAccess     | Full permissions for APIG. Users granted these permissions can use all functions of **dedicated** gateways. | System-defined policy | None       |
   +---------------------+-------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | APIG ReadOnlyAccess | Read-only permissions for APIG. Users granted these permissions can only view **dedicated** gateways.       | System-defined policy | None       |
   +---------------------+-------------------------------------------------------------------------------------------------------------+-----------------------+------------+

Process Flow
------------

.. _apig-ug-190529109__en-us_topic_0172480077_en-us_topic_0170877287_fig15451536531:

.. figure:: /_static/images/en-us_image_0000001142758280.png
   :alt: **Figure 1** Process for granting APIG permissions

   **Figure 1** Process for granting APIG permissions

#. .. _apig-ug-190529109__en-us_topic_0172480077_en-us_topic_0170877287_li10176121316284:

   Create a user group and assign permissions.

   Create a user group on the IAM console, and attach the **APIG Administrator** role or the **APIG FullAccess** policy to the group.

#. Create an IAM user.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <apig-ug-190529109__en-us_topic_0172480077_en-us_topic_0170877287_li10176121316284>`.

#. Log in and verify permissions.

   Log in to the APIG console as the created user, and verify that the user has administrator permissions for APIG.
