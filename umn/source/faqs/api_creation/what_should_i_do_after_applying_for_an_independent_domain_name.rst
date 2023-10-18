:original_name: apig-faq-2005009.html

.. _apig-faq-2005009:

What Should I Do After Applying for an Independent Domain Name?
===============================================================

If you are using a dedicated gateway, add an A record that points the independent domain name to the inbound access address of the gateway. You can bind five independent domain names to an API group but can bind each independent domain name only to one API group.

.. note::

   To use a public domain name, add an A record (dedicated gateway) in Domain Name Service (DNS).

   To use a private domain name, add an A record (dedicated gateway) in the DNS service and associate the domain name with the VPC in which your backend service is located.
