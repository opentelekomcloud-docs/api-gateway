:original_name: apig-faq-0001.html

.. _apig-faq-0001:

Why Doesn't a Request Throttling Policy Take Effect?
====================================================

-  API call limit or source IP address request limit of the policy does not take effect.

   Check whether the policy has been bound to an API.

-  User request limit of the policy does not take effect.

   Check whether the API bound with the policy uses app or IAM authentication.

-  App (credential) request limit of the policy does not take effect.

   Check whether the API bound with the policy uses app authentication.
