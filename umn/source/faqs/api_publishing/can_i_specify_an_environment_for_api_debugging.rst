:original_name: apig-faq-2005027.html

.. _apig-faq-2005027:

Can I Specify an Environment for API Debugging?
===============================================

No.

APIG debugs APIs in a specific debugging environment. After debugging is completed, you need to publish your API in an environment, and use code or Postman to add the **X-Stage** header to specify the environment where you want to call the API.
