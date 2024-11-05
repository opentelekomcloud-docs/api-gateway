:original_name: apig-faq-180307001.html

.. _apig-faq-180307001:

What Are the Error Messages Returned by APIG Like?
==================================================

When receiving an API request, APIG returns a response. A similar response body is as follows:

.. code-block::

   {
       "error_code": "APIG.0101",
       "error_msg": "API does not exist or is not published in the environment.",
       "request_id": "acbc548ac6f2a0dbdb9e3518a7c0ff84"
   }

-  **"error_code"**: error code
-  **"error_msg"**: description of the error
