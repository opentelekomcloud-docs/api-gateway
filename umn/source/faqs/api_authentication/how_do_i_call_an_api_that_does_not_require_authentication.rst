:original_name: apig-faq-2005020.html

.. _apig-faq-2005020:

How Do I Call an API That Does Not Require Authentication?
==========================================================

To call APIs that do not require authentication, construct standard HTTP requests and send them to APIG.

.. note::

   APIG **transparently transmits** requests to call an API that does not require authentication to the backend service. If you want requests to be authenticated on the API backend service, you can set **Security Authentication** to **None**. The API caller transfers the fields required for authentication to the backend service, and the backend service performs authentication.
