:original_name: apig-faq-2005027.html

.. _apig-faq-2005027:

Can I Specify an Environment for API Debugging?
===============================================

During API debugging, the specific debugging environment of APIG is used by default. Therefore, you cannot specify other environments.

After debugging is completed, you need to publish your API in an environment, and use code or Postman to add the X-Stage header to specify the environment where you want to call the API.
