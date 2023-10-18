:original_name: apig-en-faq-180307003.html

.. _apig-en-faq-180307003:

How Can I Protect My APIs?
==========================

-  Identity authentication

   Configure IAM or App authentication for APIs to prevent malicious calling.

-  Access control policies

   Configure a whitelist or blacklist of IP addresses/IP address ranges or accounts for APIs to secure access.

-  Request throttling policies

   By default, an API can be called up to 200 times per second. If your backend service does not support this access rate, decrease the quota accordingly.
