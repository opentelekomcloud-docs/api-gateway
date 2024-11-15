:original_name: apig_03_0001.html

.. _apig_03_0001:

Overview
========

APIG is a fully managed service that enables you to securely build, manage, and deploy APIs at any scale with high performance and availability. With APIG, you can easily integrate your internal service systems and selectively expose and monetize your service capabilities.

General Procedure
-----------------

The following figure shows the procedure for using APIG to host APIs.


.. figure:: /_static/images/en-us_image_0000001184670172.png
   :alt: **Figure 1** APIG

   **Figure 1** APIG

You can :ref:`expose your API services <apig_03_0001__en-us_topic_0000001175975948_section95109458338>` or :ref:`obtain and call APIs of others <apig_03_0001__en-us_topic_0000001175975948_section137574138345>` through APIG.

.. _apig_03_0001__en-us_topic_0000001175975948_section95109458338:

Exposing APIs
-------------

Enterprises or developers selectively expose and monetize their services and data through APIG.


.. figure:: /_static/images/en-us_image_0000001524872816.png
   :alt: **Figure 2** API exposing process

   **Figure 2** API exposing process

#. :ref:`Create a gateway. <apig_03_0037>`

   A gateway is an independent resource space where all operations are performed. Resources of different gateways are isolated from each other.

#. :ref:`Create an API group <apig_03_0005>`.

   Each API belongs to an API group. Create an API group before creating an API.

#. :ref:`Bind a domain name. <apig_03_0006>`

   Before exposing an API, bind an independent domain name to the target group so that API callers can access the API.

   You can debug the API using the debugging domain name allocated to the group to which the API belongs. The domain name can be accessed a maximum of 1000 times every day.

#. :ref:`Create an API. <apig_03_0010>`

   Encapsulate existing backend services into standard RESTful APIs and expose them to external systems.

   After creating an API, configure the following settings to control API access:

   -  Traditional policies

      -  :ref:`Request throttling <apig_03_0025>`

         Request throttling controls the number of times an API can be called within a time period to protect backend services.

      -  :ref:`Access control <apig_03_0027>`

         Set a blacklist or whitelist to deny or allow API access from specific IP addresses or accounts.

      -  :ref:`Signature keys <apig_03_0028>`

         Signature keys are used by backend services to verify the identity of APIG.

   -  Plug-in policies

      -  :ref:`CORS <apig_03_0021>`

         This policy provides the capabilities of specifying preflight request headers and response headers and automatically creating preflight request APIs for cross-origin API access.

      -  :ref:`HTTP Response Header Management <apig_03_0022>`

         You can customize HTTP response headers that will be contained in an API response.

      -  :ref:`Request Throttling 2.0 <apig_03_0054>`

         This policy enables you to limit the number of times an API can be called within a specific time period. Parameter-based, basic, and excluded throttling is supported.

      -  :ref:`Kafka Log Push <apig_03_0061>`

         This policy pushes API calling logs to Kafka so that users can easily obtain them.

      -  :ref:`Circuit Breaker <apig_03_0023>`

         This policy protects your backend service when a performance issue occurs.

      -  :ref:`Third-Party Authorizer <apig_03_0077>`

         You can configure your own service to authenticate API requests.

#. :ref:`Debug the API. <apig_03_0012>`

   Verify whether the API is working normally.

#. :ref:`Publish the API. <apig_03_0014>`

   The API can be called only after it has been published in an environment.

.. _apig_03_0001__en-us_topic_0000001175975948_section137574138345:

Calling APIs
------------

Enterprises and developers obtain and call APIs of other providers, thereby reducing development time and costs.


.. figure:: /_static/images/en-us_image_0000001227056681.png
   :alt: **Figure 3** API calling process

   **Figure 3** API calling process

#. :ref:`Obtain an API. <apig_03_0046__en-us_topic_0000001606053745_section3363103010129>`

   Obtain the API request information, including the domain name, protocol, method, path, and authentication mode.

#. :ref:`Create a credential. <apig_03_0030>`

   For an API that uses app authentication, create a credential to generate a credential ID and key/secret pair. Bind the credential to the API so that you can call the API through app authentication.

#. Obtain an SDK.

   Use the SDK to generate a signature for the AK/SK and call the API.

#. :ref:`Call the API. <apig_03_0046__en-us_topic_0000001606053745_section19907427165210>`

   Call the API using its access address and perform authentication based on its authentication mode.
