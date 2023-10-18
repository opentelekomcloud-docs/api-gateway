:original_name: apig-ug-0017.html

.. _apig-ug-0017:

What Is APIG?
=============

API Gateway (APIG) is a high-performance, high-availability, and high-security API hosting service that helps you build, manage, and deploy APIs at any scale. With just a few clicks, you can integrate internal systems, and selectively expose capabilities with minimal costs and risks.

-  To monetize your service and data capabilities, you can open them up by creating APIs in APIG. Then you can provide the APIs for API callers using offline channels.
-  You can also obtain open APIs from APIG to reduce your development time and costs.


.. figure:: /_static/images/en-us_image_0000001239189917.png
   :alt: **Figure 1** APIG architecture

   **Figure 1** APIG architecture

Product Functions
-----------------

-  **API lifecycle management**

   The lifecycle of an API involves creating, publishing, removing, and deleting the API. API lifecycle management enables you to quickly and efficiently expose service capabilities.

-  **Cloud native gateway**

   APIG integrates traffic ingress (Kubernetes Ingress) and microservice governance (Kubernetes Gateway API) in one gateway, improving performance, simplifying the architecture, and reducing deployment and O&M costs.

-  **Built-in debugging tool**

   With the built-in debugging tool, you can debug APIs using different HTTP headers and request bodies. This tool simplifies the API development process and reduces the API development and maintenance costs.

-  **Version management**

   An API can be published in different environments. Publishing an API again in the same environment will override the API's previous version. APIG displays the publication history (including the version, description, date and time, and environment) of each API. You can roll back an API to any historical version to meet dark launch and version upgrade requirements.

-  **Environment variables**

   Environment variables are manageable and specific to environments. Variables of an API will be replaced by the values of the variables in the environment where the API will be published. You can create variables in different environments to call different backend services using the same API.

-  **Request throttling**

   -  For different services and users, you can control the request frequency at which an API can be called by a user, an app, and an IP address. This ensures that backend services can run stably.
   -  The throttling can be accurate to the second, minute, hour, or day.
   -  Excluded apps and tenants can be configured to limit the number of API calls from specific apps and tenants, respectively.

-  **Monitoring and alarm**

   APIG provides visualized, real-time API monitoring, and displays multiple metrics, including number of requests, invocation latency, and number of errors. The metrics help you understand the API usage, allowing you to identify potential service risks.

-  **Access control**

   Access control policies are one of the security measures provided by APIG. They allow or deny API access from specific IP addresses or accounts.

-  **VPC channels**

   VPC channels can be created for accessing resources in Virtual Private Clouds (VPCs) and exposing capabilities of backend services deployed in VPCs. A VPC channel forwards API requests to different servers for load balancing.

-  **Signature keys**

   A signature key consists of a key and secret, and takes effect only after being bound to APIs. Signature keys are used by backend services to verify the identity of APIG and ensure secure access.

-  **Mock response**

   Mock backends simulate API responses for circuit breakers, service degradation, and redirection.
