:original_name: apig-en-api-180713204.html

.. _apig-en-api-180713204:

Pagination Query
================

APIG supports pagination query of resource lists, such as an API list.

To perform a pagination query, add the following parameters to the URL:

-  **page_size**: number of records to be displayed on each page. If this parameter is not specified, the default value **20** is used. The maximum value is **500**.
-  **page_no**: page number for displaying query results.

Example:

.. code-block:: text

   GET /v1.0/apigw/apis?page_size=10&page_no=5
