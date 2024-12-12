:original_name: apig-faq-0008.html

.. _apig-faq-0008:

Are Client IP Addresses Verified for Access Control?
====================================================

Not necessarily.

In APIG, access control is based on the value of **$remote_addr**. **$remote_addr** indicates a client IP address and is determined by the access mode. If a client accesses APIG without using any proxy, **remote_addr** is the client's IP address. If a client accesses APIG using a proxy, the client first accesses the proxy, and the proxy then forwards the request to APIG. In this case, **remote_addr** is the proxy's IP address.
