:original_name: apig-faq-180307009.html

.. _apig-faq-180307009:

How Do I Ensure the Security of Backend Services Invoked by APIG?
=================================================================

You can ensure the security of backend services invoked by APIG by using the following methods:

-  Bind signature keys to APIs

   After a signature key is bound to an API, APIG adds signature information to each request sent to the backend service. The backend service calculates the signature information in each request and checks whether the signature information is consistent with that on APIG.

-  Encrypt requests using HTTPS

   Ensure that the required SSL certificate exists.

-  Perform backend authentication

   Enable security authentication for backend services of the desired APIs to process only API requests that carry correct authentication information.
