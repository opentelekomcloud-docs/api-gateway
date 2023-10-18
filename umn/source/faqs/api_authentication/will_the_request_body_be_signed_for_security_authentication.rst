:original_name: apig-faq-2005018.html

.. _apig-faq-2005018:

Will the Request Body Be Signed for Security Authentication?
============================================================

Yes. The request body is another element that needs to be signed in addition to the mandatory request header parameters. For example, when an API used to upload a file using the POST method is called, the hash value of the file to upload is calculated to generate a signature.

For details about signatures, see section "App Authentication" in the *API Gateway Developer Guide*.
