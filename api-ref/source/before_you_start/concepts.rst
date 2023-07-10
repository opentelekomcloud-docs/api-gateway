:original_name: apig-api-190529267.html

.. _apig-api-190529267:

Concepts
========

-  Account

   An account is created upon successful registration with the cloud system. The account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The account is a payment entity and should not be used directly to perform routine management. For security purposes, create IAM users and grant them permissions for routine management.

-  IAM user

   An IAM user is created using an account to use cloud services. Each IAM user has its own identity credentials (password and access keys).

   An IAM user can view the account ID and user ID on the **My Credentials** page of the console. The account name, username, and password will be required for API authentication.

-  Region

   Regions are defined by their geographical location and network latency. Public services, such as Elastic Cloud Server (ECS), Elastic Volume Service (EVS), and Object Storage Service (OBS), are shared within the same region. There are universal regions and dedicated regions. A universal region serves all tenants, while a dedicated region serves specific tenants.

-  AZ

   AZs are physically isolated locations in a region, but are interconnected through an internal network for enhanced application availability.

-  Project

   Projects group and isolate resources (including compute, storage, and network resources) across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. For more refined access control, create subprojects under a project. Users can then be assigned permissions to access only specific resources in the subprojects.


   .. figure:: /_static/images/en-us_image_0172290304.gif
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model
