:original_name: apig-ug-180307011.html

.. _apig-ug-180307011:

Calling an API
==============

Use the API test tool to configure the API request and authentication. For details about how to call an API, see section "Calling Published APIs" > :ref:`Calling APIs <apig_03_0046>`.

#. Obtain the API request information and construct the API URL.

   For illustration purposes, an API and its documentation are obtained through offline channels. You can also obtain the authentication mode, request method, request path, and other information about the API.

#. Add the header parameter **X-Apig-AppCode** and set the parameter value to the :ref:`generated AppCode <apig-ug-180307009>`.

#. Add the header parameter **x-stage** and set the parameter value to the :ref:`running environment <apig-ug-180307004>`. Skip this step if the API has been published in the RELEASE environment.

#. Click **Send** to send a request.

   If the API is called successfully, **200 OK** is displayed. Otherwise, rectify the fault by referring to :ref:`Error Codes <apig_03_0048>`.

   |image1|

.. |image1| image:: /_static/images/en-us_image_0000001316742126.png
