:original_name: apig-en-ug-180307002.html

.. _apig-en-ug-180307002:

Process Flow
============

The following figure shows the process of exposing an API.

|image1|

#. Creating a Gateway

   Buy a dedicated gateway. For details, see :ref:`Buying a Dedicated Gateway <apig-ug-191004>`.

#. :ref:`Creating an API Group <apig-en-ug-180307003>`

   An API group facilitates management of APIs used for the same service. Create an API group and then create APIs.

#. :ref:`Binding a Domain Name <apig-ug-190419107>`

   Before making the API available for users to access, bind an independent domain name (custom domain name) to the group to which the API belongs. Then API callers can use these domain names to call the API.

#. :ref:`Creating an API <en-us_topic_0080101678>`

   When creating an API, configure the frontend and backend request paths, parameters, and protocols.

#. :ref:`Debugging an API <apig-ug-190419108>`

   Debug the API to check whether it works normally.

#. :ref:`(Optional) Creating an Environment <apig-en-ug-180307004>`

   An API can be called in different scenarios, such as the production environment (RELEASE) or other custom environments. RELEASE is the default environment defined in APIG.

#. :ref:`Publishing an API <apig-en-ug-180307005>`

   Publish the API so that it can be called.

.. |image1| image:: /_static/images/en-us_image_0000001182465263.png
