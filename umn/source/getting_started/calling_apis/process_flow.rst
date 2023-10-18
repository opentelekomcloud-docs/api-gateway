:original_name: apig-en-ug-180307008.html

.. _apig-en-ug-180307008:

Process Flow
============

The following figure shows the process of calling an API.

|image1|

#. Obtaining an API

   Obtain an API and its documentation from an API provider.

#. :ref:`Creating an App and Getting Authorized <apig-en-ug-180307010>`

   APIs that use app authentication can only be called using apps bound to them.

#. :ref:`Adding an AppCode for Simple Authentication <apig-en-ug-180307009>`

   APIG only verifies the AppCode during simple authentication.

#. :ref:`Calling the API <apig-en-ug-180307011>`

   Use an API test tool to call the API with app authentication credentials.

.. |image1| image:: /_static/images/en-us_image_0000001142638662.png
