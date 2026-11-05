:original_name: apig_03_0127.html

.. _apig_03_0127:

Process Flow
============

Enterprises or developers selectively expose and monetize their services and data through APIG.

|image1|

#. :ref:`Creating an API Group <apig_03_0005>`

   Each API belongs to an API group. Create an API group before creating an API.

#. :ref:`Adding an SSL Certificate for an API <apig_03_0055>`

   If the API group contains HTTPS-compatible APIs, add an SSL certificate for the independent domain name bound to the group. Otherwise, skip this step.

#. :ref:`Configuring the Domain Name for Calling APIs <apig_03_0006>`

   Before exposing an API, bind an independent domain name to the target group so that API callers can access the API.

   You can debug the API using the debugging domain name allocated to the group to which the API belongs. The domain name can be accessed a maximum of 1000 times every day. **It is for debugging only, not for production.**

#. :ref:`(Optional) Creating a Load Balance Channel <apig_03_0040>`

   To access a backend service deployed on a specified server, you can create a load balance channel. Otherwise, skip this step.

#. :ref:`Creating an API <apig_03_0128>`

   Encapsulate existing backend services into standard RESTful or gRPC APIs and expose them to external systems.

   After APIs are created, perform operations in :ref:`Configuring API Policies <apig_03_0019>` and :ref:`Managing APIs <apig_03_0003>` based on service requirements.

#. :ref:`Debugging an API <apig_03_0012>`

   Verify that the API service functions are normal using the online debugging provided by APIG.

#. :ref:`(Optional) Configuring the Environment and Environment Variables <apig_03_0007>`

   An API can be called in different environments, such as production, testing, and development environments. The RELEASE environment is the default environment. If you use the RELEASE environment, skip this step.

   If environment variables are defined in backend information of an API, you need to add the variables to the environment. You can create variables in different environments to call different backend services using the same API.

#. :ref:`Publishing an API <apig_03_0014>`

   The API can be called only after it has been published in an environment.

.. |image1| image:: /_static/images/en-us_image_0000002103465158.png
