:original_name: apig-faq-19123002.html

.. _apig-faq-19123002:

Why Am I Seeing the Error Message "The API does not exist or has not been published in the environment" When I Call an API?
===========================================================================================================================

If an open API in APIG failed to be called, troubleshoot the failure by performing the following operations:

#. The domain name, request method, or path used for calling the API is incorrect.

   -  For example, an API created using the POST method is called with GET.
   -  Missing a slash (/) in the access URL will lead to a failure in matching the URL in the API details. For example, URLs **http://7383ea59c0cd49a2b61d0fd1d351a619.apigw.region.cloud.com/test/** and **http://7383ea59c0cd49a2b61d0fd1d351a619.apigw.region.cloud.com/test** represent two different APIs.

#. The API has not been published. APIs can be called only after they have been published in an environment. For details, see :ref:`Publishing an API <apig_03_0014>`. If the API has been published in a non-production environment, check whether the **X-Stage** header in the request is the name of the environment.
#. The domain name is resolved incorrectly. If the domain name, request method, and path for calling the API are correct and the API has been published in an environment, the API may not be correctly resolved to the group to which the API belongs. For example, if you have multiple API groups and each group has an independent domain name, the API may be called using the independent domain name of another group. Ensure that the API is being called using the correct domain name.
#. Check whether the API allows OPTIONS cross-region requests. If yes, enable cross-origin resource sharing (CORS) for the API, and create an API that uses the OPTIONS method. For details, see :ref:`CORS Calling of an Open API <apig_03_0011>`.
