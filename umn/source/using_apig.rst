:original_name: en-us_topic_0080101651.html

.. _en-us_topic_0080101651:

Using APIG
==========

API Gateway (APIG) is a fully managed service that enables you to securely build, manage, and deploy APIs at any scale with high performance and availability. With APIG, you can easily integrate your internal service systems and selectively expose your service capabilities through its **API opening** and **API calling** functions.

-  **API Opening**

   Enterprises and developers selectively expose their services and data through APIG.


   .. figure:: /_static/images/en-us_image_0000001130693484.png
      :alt: **Figure 1** API opening

      **Figure 1** API opening

   The following figure shows the API opening process.


   .. figure:: /_static/images/en-us_image_0000001188797557.png
      :alt: **Figure 2** API opening process

      **Figure 2** API opening process

   #. Create a gateway.

      :ref:`Buy a dedicated gateway <apig-ug-191004>`.

   #. :ref:`Create an API group <apig-en-ug-180307015>`.

      Each API belongs to an API group. Create a group before creating an API.

   #. :ref:`Bind a domain name <apig-en-ug-180327076>`.

      Before exposing an API, bind an independent domain name to the group so that users can access the API.

      You can debug the API using the default subdomain name allocated to the group to which the API belongs. The subdomain name can be called a maximum of 1000 times every day.

   #. :ref:`Create an API <apig-en-ug-180307020>`.

      Encapsulate existing backend services into standard RESTful APIs and expose them to external systems.

      After creating an API, configure the following settings to control API access:

      -  :ref:`Request throttling <apig-en-ug-180307028>`

         Set the maximum number of times the API can be called within a time period to protect backend services.

      -  :ref:`Access control <apig-en-ug-180712096>`

         Set a blacklist or whitelist to deny or allow API access from specific IP addresses or accounts.

      -  :ref:`Signature keys <apig-en-ug-180307040>`

         Signature keys are used by backend services to verify the identity of APIG and ensure secure access.

   #. :ref:`Debug the API <apig-en-ug-180307025>`.

      Verify whether the API is working normally.

   #. :ref:`Publish the API <apig-en-ug-180307023>`.

      The API can be called only after it has been published in an environment.

-  **API calling**

   Enterprises and developers obtain and call APIs of other providers, thereby reducing development time and costs.


   .. figure:: /_static/images/en-us_image_0000001130533706.png
      :alt: **Figure 3** API calling

      **Figure 3** API calling

   The following figure shows the API calling process.


   .. figure:: /_static/images/en-us_image_0000001188656221.png
      :alt: **Figure 4** API calling process

      **Figure 4** API calling process

   #. :ref:`Obtain an API <apig-ug-0011__section15668112016810>`.

      Obtain the API request information, including the domain name, protocol, method, path, and authentication mode.

   #. :ref:`Create an app <apig-en-ug-180307049>`.

      For an API that uses app authentication, create an app to generate an AppKey and AppSecret. Bind the app to the API so that you can call the API through app authentication.

   #. Obtain an SDK.

      Use the SDK to generate a signature for the AK/SK and call the API.

   #. :ref:`Call the API <apig-ug-0011__section14411121782210>`.

      Obtain the API using its access address and perform authentication based on its authentication mode.
