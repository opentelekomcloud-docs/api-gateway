:original_name: apig-api-190529263.html

.. _apig-api-190529263:

Before You Start
================

API Gateway (APIG) is a high-performance, high-availability, and high-security API hosting service that helps enterprises build, manage, and deploy APIs at any scale.

This document describes how to use REST APIs to perform operations on APIG, such as creating, deleting, and modify your own APIs.

If you plan to access API Gateway through APIs, ensure that you are familiar with API Gateway concepts. For details, see the *User Guide*.

.. _apig-api-190529263__en-us_topic_0000001969180093_section932113578479:

Endpoints
---------

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. For the endpoints of all services, contact technical support engineers.

Concepts
--------

-  Account

   An account is created upon successful registration. The account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The account is a payment entity and should not be used directly to perform routine management. For security purposes, create IAM users and grant them permissions for routine management.

-  IAM user

   A user is created using a domain to use cloud services. Each user has its own identity credentials (password and access keys).

   An IAM user can view the account ID and user ID on the **My Credentials** page of the console. The domain name, username, and password will be required for API authentication.

-  Region

   Regions are divided based on geographical location and network latency. Public services, such as Elastic Cloud Server (ECS), Elastic Volume Service (EVS), Object Storage Service (OBS), Virtual Private Cloud (VPC), Elastic IP (EIP), and Image Management Service (IMS), are shared within the same region. Regions are classified into universal and dedicated regions. A universal region provides universal cloud services for common tenants. A dedicated region provides specific services for specific tenants.

   For details, see **Help Center > Others > FAQs > Regions and AZs**.

-  Availability zone (AZ)

   An Availability Zone (AZ) contains one or more physical data centers. Each AZ has independent cooling, fire extinguishing, moisture-proof, and electricity facilities. Within an AZ, compute, network, storage, and other resources are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to support cross-AZ high-availability systems.

-  Project

   Projects group and isolate resources (including compute, storage, and network resources) across physical regions. A default project is provided for each region, and subprojects can be created under each default project. Users can be granted permissions to access all resources in a specific project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in the specific subprojects.


   .. figure:: /_static/images/en-us_image_0000001988900321.png
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model

   An IAM user can view the project ID on the **My Credentials** page of the console.

-  Enterprise project

   Enterprise projects group and manage resources across regions. Resources in different enterprise projects are logically isolated. An enterprise project can contain resources of multiple regions, and resources can be added to or removed from enterprise projects.

   For details about how to obtain enterprise project IDs and features, see the *Enterprise Management Service User Guide*.
