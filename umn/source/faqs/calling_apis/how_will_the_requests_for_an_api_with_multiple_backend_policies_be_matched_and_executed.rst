:original_name: apig-faq-19123001.html

.. _apig-faq-19123001:

How Will the Requests for an API with Multiple Backend Policies Be Matched and Executed?
========================================================================================

If multiple backend policies are configured for an API, APIG will match the backend policies in sequence. If an API request matches one of the backend policies, APIG immediately forwards the request to the corresponding backend and stops matching.

If no backend policy is matched, the API request is forwarded to the default backend server.
