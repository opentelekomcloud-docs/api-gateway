:original_name: apig-pd-190529006.html

.. _apig-pd-190529006:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your APIG resources, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your resources.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to the employees to control their access to specific resources.

If your account does not require individual IAM users for permissions management, skip this chapter.

APIG Permissions
----------------

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and attach policies or roles to these groups. The user then inherits permissions from the groups to which the user belongs, and can perform specified operations on cloud services based on the permissions.

APIG is a project-level service deployed and accessed in specific physical regions. To assign APIG permissions to a user group, you need to specify region-specific projects for which the permissions will take effect. If you select **All projects**, the permissions will be granted for both the global service project and all region-specific projects. When accessing APIG, the users need to switch to a region where they have been authorized to use this service.

You can grant permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other dependent roles for permissions to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization and meets requirements for secure access control. For example, you can grant APIG users only the permissions for performing specific operations. Most policies define permissions based on APIs. For the API actions supported by APIG, see section "Permissions Policies and Supported Actions" in the *API Reference*.

:ref:`Table 1 <apig-pd-190529006__en-us_topic_0172474100_table1934161212122>` lists all the system-defined roles and policies supported by APIG.

.. _apig-pd-190529006__en-us_topic_0172474100_table1934161212122:

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

You can view the content of the preceding roles and policies on the IAM console. For example, the content of the **APIG FullAccess** policy is as follows:

.. code-block::

   {
       "Version": "1.1",
       "Statement": [
           {
               "Action": [
                   "apig:*:*",
                   "vpc:*:get*",
                   "vpc:*:list*",
                   "vpc:ports:create",
                   "vpc:ports:update",
                   "vpc:ports:delete",
                   "vpc:publicIps:update",
                   "FunctionGraph:function:listVersion",
                   "FunctionGraph:function:list",
                   "FunctionGraph:function:getConfig",
                   "ecs:servers:list",
                   "lts:groups:list",
                   "lts:logs:list",
                   "lts:topics:list"
               ],
               "Effect": "Allow"
           }
       ]
   }

Related Documents
-----------------

-  Section "Service Overview" in the *Identity and Access Management User Guide*
-  Section "Creating a User and Granting Permissions" in the *API Gateway User Guide*
