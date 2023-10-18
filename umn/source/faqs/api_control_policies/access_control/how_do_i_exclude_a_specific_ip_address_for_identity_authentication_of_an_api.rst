:original_name: apig-faq-2005023.html

.. _apig-faq-2005023:

How Do I Exclude a Specific IP Address for Identity Authentication of an API?
=============================================================================

You can choose either of the following solutions:

-  Solution 1: Create an API that does not require authentication, and configure an access control policy to whitelist the IP address.
-  Solution 2: Create two APIs, one that uses IAM or app authentication and one that does not require authentication, and configure an access control policy to whitelist the IP address for the API that does not require authentication.
