:original_name: apig-faq-2005013.html

.. _apig-faq-2005013:

Does APIG Support HTTPS Two-Way Authentication?
===============================================

Dedicated gateway: Yes.

-  Frontend two-way authentication: When binding an independent domain name, select an :ref:`SSL certificate <apig_03_0055>` that contains a CA certificate. Client authentication, that is, two-way authentication, can be enabled.
-  Backend two-way authentication: When creating an API, enable two-way authentication for the backend service. For details, see the description about **Two-Way Authentication** in :ref:`Creating an API <apig_03_0010>`.
