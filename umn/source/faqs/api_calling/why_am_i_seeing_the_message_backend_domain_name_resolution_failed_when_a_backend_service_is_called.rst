:original_name: apig-faq-0004.html

.. _apig-faq-0004:

Why Am I Seeing the Message "Backend domain name resolution failed" When a Backend Service Is Called?
=====================================================================================================

An error message indicating a domain name resolution failure is displayed when the backend service is called, although private domain name resolution is completed for the VPC where the API gateway is located.

**Possible Cause**

The VPC of the API gateway is isolated from that of the backend service. Private domain names can be resolved only for the VPC of the backend service.

**Solution**

-  Method 1: When creating an API, set **Backend Address** to a public network domain name.

-  Method 2: When creating an API, do not use a VPC channel. Instead, set **Backend Address** to the backend service IP address, and add a constant parameter to specify the **Host** field in the header.

   |image1|

-  Method 3: When creating an API, specify a VPC channel.

   #. Create a VPC channel.

      |image2|

   #. Add the backend service address.

      |image3|

   #. When creating an API, select the VPC channel and configure a custom header.

      |image4|

.. |image1| image:: /_static/images/en-us_image_0000001180286140.png
.. |image2| image:: /_static/images/en-us_image_0000001225404945.png
.. |image3| image:: /_static/images/en-us_image_0000001179806978.png
.. |image4| image:: /_static/images/en-us_image_0000001224966973.png
