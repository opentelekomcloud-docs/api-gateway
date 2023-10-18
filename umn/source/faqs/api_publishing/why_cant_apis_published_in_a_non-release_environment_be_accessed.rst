:original_name: apig-en-faq-180606011.html

.. _apig-en-faq-180606011:

Why Can't APIs Published in a Non-RELEASE Environment Be Accessed?
==================================================================

To make an API published in a non-RELEASE environment accessible, add the **x-stage** header to the API request.

Example:

.. code-block::

   r.Header.Add("x-stage", "RELEASE")
