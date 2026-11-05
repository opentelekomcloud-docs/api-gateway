:original_name: apig_03_0001.html

.. _apig_03_0001:

Process of Using APIG
=====================

APIG is a fully managed service that enables you to securely build, manage, and deploy APIs at any scale with high performance and availability. With APIG, you can easily integrate your internal service systems and selectively expose and monetize your service capabilities.

General Procedure
-----------------

The following figure shows the procedure for using APIG to host APIs.


.. figure:: /_static/images/en-us_image_0000002586181487.png
   :alt: **Figure 1** Process of using APIG

   **Figure 1** Process of using APIG

#. :ref:`Creating a User and Granting APIG Permissions <apig_03_0050>`

   Create a user and grant APIG permissions with IAM. If the preset permissions do not meet requirements, you can create custom policies.

#. :ref:`Creating a Gateway <apig_03_0037>`

   A gateway is an independent resource space where all operations are performed. Resources of different gateways are isolated from each other. To open APIs for external services, you need to create a gateway first.

   After a gateway is created, you can :ref:`configure its parameters <apig_03_0039>`, classify resources by group (:ref:`Configuring Gateway Tags <apig_03_0075>`), and connect the VPC endpoint to the VPC endpoint service (:ref:`Configuring Gateway VPC Endpoints <apig_03_0063>`). For more operations, see :ref:`Managing APIG Gateways <apig_03_0035>`.

#. :ref:`Opening APIs <apig_03_0126>`

   Open services and data by directly providing open APIs to API callers or releasing them on KooGallery for monetization.

   To use your own authentication system for API calling, perform operations in :ref:`Configuring Custom API Authentication <apig_03_0029>`. To orchestrate API parameters, perform operations in :ref:`Configuring API Parameter Orchestration Rules <apig_03_0110>`. To customize API error responses, perform operations in :ref:`Customizing Error Response for APIs <apig_03_0008>`. For more operations, see :ref:`Managing APIs <apig_03_0003>`.

#. :ref:`(Optional) Configuring Authorization for API Calling <apig_03_0129>`

   Credentials need to be authorized to call APIs that use App authentication. API callers use the key and secret to authenticate API requests. They can also use the AppCode for simple authentication.

   If you want to limit the number of API calls made by an API caller in a specified period, you can perform operations in :ref:`Credential Quota Policy <apig_03_0059>`. If you want to control the IP addresses that can access an API, you can perform operations in :ref:`Credential Access Control Policy <apig_03_0060>`.

#. :ref:`Calling APIs <apig_03_0045>`

   Obtain the API and its access address to call the API. Authentication operations need to be performed depending on the authentication mode.
