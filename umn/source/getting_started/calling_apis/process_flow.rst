:original_name: apig-ug-180307008.html

.. _apig-ug-180307008:

Process Flow
============

The following figure shows the process of calling an API.

|image1|

#. Obtaining an API

   Obtain an API and its documentation from an API provider.

#. :ref:`Creating a Credential and Getting Authorized <apig-ug-180307010>`

   APIs that use app authentication can only be called using credentials bound to them.

#. :ref:`Adding an AppCode for Simple Authentication <apig-ug-180307009>`

   API Gateway only verifies the AppCode during simple authentication.

#. :ref:`Calling an API <apig-ug-180307011>`

   Use an API test tool to call the API with the simple authentication AppCode.

.. |image1| image:: /_static/images/en-us_image_0000001368310257.png
