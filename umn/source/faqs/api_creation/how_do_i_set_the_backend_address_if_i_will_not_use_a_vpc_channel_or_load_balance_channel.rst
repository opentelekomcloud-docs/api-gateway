:original_name: apig-faq-2005004.html

.. _apig-faq-2005004:

How Do I Set the Backend Address If I Will Not Use a VPC Channel (or Load Balance Channel)?
===========================================================================================

Specify the backend address as a public domain name or a public IP address, such as the Elastic IP (EIP) of an Elastic Cloud Server (ECS). To do this, enable public outbound access for the gateway.

Use a private network IP address, not a private network domain name.
