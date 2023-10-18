:original_name: apig-en-ug-180307011.html

.. _apig-en-ug-180307011:

Calling an API
==============

Use an API test tool to configure the API calling information.

#. Obtain the API request information.

   For illustration purposes, an API and its documentation are obtained through offline channels. You can also obtain the authentication mode, request method, request path, and other information about the API.

#. Add the header parameter **X-Apig-AppCode** and set the parameter value to the :ref:`generated AppCode <apig-en-ug-180307009>`.

#. Add the header parameter **x-stage** and set the parameter value to the :ref:`running environment <apig-en-ug-180307004>`. Skip this step if the API has been published in the RELEASE environment.

#. Click **Send** to send a request.

   If the API is called successfully, the message **200 OK** is displayed.

   |image1|

.. |image1| image:: /_static/images/en-us_image_0000001188579631.png
