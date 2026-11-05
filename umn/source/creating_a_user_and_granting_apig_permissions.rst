:original_name: apig_03_0050.html

.. _apig_03_0050:

Creating a User and Granting APIG Permissions
=============================================

This topic describes how to use `Identity and Access Management <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0001.html>`__ (IAM) to implement fine-grained permissions control for your APIG resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing APIG resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust another account or cloud service to perform O&M on your APIG resources.

If your account does not require individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <apig_03_0050__en-us_topic_0172480077_en-us_topic_0170877287_fig15451536531>`).

Prerequisites
-------------

Learn about the permissions (see :ref:`Table 1 <apig_03_0050__en-us_topic_0172480077_table13382143731910>`) supported by APIG and choose policies or roles according to your requirements.

.. _apig_03_0050__en-us_topic_0172480077_table13382143731910:

.. table:: **Table 1** System-defined roles and policies supported by APIG

   +---------------------+----------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Role/Policy Name    | Description                                                                                        | Type                  | Dependency                                                                                                                                                                           |
   +=====================+====================================================================================================+=======================+======================================================================================================================================================================================+
   | APIG Administrator  | Administrator permissions for APIG. Users granted these permissions can use all functions of APIG. | System-defined role   | If a user needs to create, delete, or change resources of other services, the user must also be granted administrator permissions of the corresponding services in the same project. |
   +---------------------+----------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | APIG FullAccess     | Full permissions for APIG. Users granted these permissions can use all functions of APIG.          | System-defined policy | None                                                                                                                                                                                 |
   +---------------------+----------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | APIG ReadOnlyAccess | Read-only permissions for APIG. Users granted these permissions can only view APIG.                | System-defined policy | None                                                                                                                                                                                 |
   +---------------------+----------------------------------------------------------------------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Process Flow
------------

.. _apig_03_0050__en-us_topic_0172480077_en-us_topic_0170877287_fig15451536531:

.. figure:: /_static/images/en-us_image_0000002236177094.png
   :alt: **Figure 1** Process for granting APIG permissions

   **Figure 1** Process for granting APIG permissions

#. .. _apig_03_0050__en-us_topic_0172480077_en-us_topic_0170877287_li10176121316284:

   `Create a user group and assign permissions <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0046611269.html>`__.

   Create a user group on the IAM console, and attach the **APIG Administrator** role or the **APIG FullAccess** policy to the group.

#. `Create an IAM user <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0046611303.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <apig_03_0050__en-us_topic_0172480077_en-us_topic_0170877287_li10176121316284>`.

#. `Log in <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0552.html>`__ and verify permissions.

   Log in to the APIG console as the created user, and verify that the user has administrator permissions for APIG.

.. _apig_03_0050__section045282915216:

Custom APIG Policies
--------------------

Custom policies can be created to supplement the system-defined policies of APIG. For the actions that can be added to custom policies, see `Permissions Policies and Supported Actions <https://docs.otc.t-systems.com/api/apig/api-grant-policy.html>`__.

You can create custom policies using one of the following methods:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Create a JSON policy or edit an existing one.

For operation details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0016.html>`__. The following section contains examples of common APIG custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allow users to create and debug APIs

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "
                           apig:apis:create
                           apig:apis:debug
                       "
                  ]
              }
          ]
      }

-  Example 2: Deny API group creation

   A policy with only "Deny" permissions must be used together with other policies. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **APIG FullAccess** policy to a user but you want to prevent the user from creating API groups. Create a custom policy for denying API group creation, and attach both policies to the group to which the user belongs. Then, the user can perform all operations on API gateways except creating API groups. The following is an example of a deny policy:

   .. code-block::

      {
          "Version": "1.1",
          "Statement": [
              {
                  "Effect": "Allow",
                  "Action": [
                      "
                           apig:apis:create
                           apig:apis:debug
                       "
                  ]
              }
          ]
      }
