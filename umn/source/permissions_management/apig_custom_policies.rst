:original_name: apig_03_0051.html

.. _apig_03_0051:

APIG Custom Policies
====================

Custom policies can be created to supplement the system-defined policies of APIG. For the actions that can be added to custom policies, see .

You can create custom policies using one of the following methods:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For operation details, see section "Creating a Custom Policy" in the *Identity and Access Management User Guide*. The following section contains examples of common APIG custom policies.

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

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

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
