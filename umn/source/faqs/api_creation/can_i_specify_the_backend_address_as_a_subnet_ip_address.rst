:original_name: apig-faq-2005006.html

.. _apig-faq-2005006:

Can I Specify the Backend Address as a Subnet IP Address?
=========================================================

If you use a dedicated gateway, you can specify either an IP address that belongs to the same subnet where the gateway is deployed, or the private address of a local data center connected to the gateway through Direct Connect.

Unsupported network segments:

-  0.0.0.0/8
-  10.0.0.0/8
-  100.125.0.0/16
-  127.0.0.0/8
-  169.254.0.0/16
-  172.16.0.0/12
-  192.0.0.0/24
-  192.0.2.0/24
-  192.88.99.0/24
-  192.168.0.0/16
-  198.18.0.0/15
-  198.51.100.0/24
-  203.0.113.0/24
-  224.0.0.0/4
-  240.0.0.0/4
-  255.255.255.255/32
