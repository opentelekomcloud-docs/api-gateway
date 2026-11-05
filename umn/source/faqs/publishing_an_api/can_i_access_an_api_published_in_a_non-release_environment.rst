:original_name: apig-faq-180606011.html

.. _apig-faq-180606011:

Can I Access an API Published in a Non-RELEASE Environment?
===========================================================

Yes. To access an API published in a non-RELEASE environment, add the **x-stage** header to the API request.

Example:

.. code-block::

   r.Header.Add("x-stage", "RELEASE")

You can also refer to the examples in :ref:`Quickly Opening and Calling APIs <apig-ug-180307002>`.
