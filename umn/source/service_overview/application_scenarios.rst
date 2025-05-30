:original_name: apig-pd-180307003.html

.. _apig-pd-180307003:

Application Scenarios
=====================

Internal System Decoupling
--------------------------

As enterprises develop rapidly with quick business changes, internal systems of enterprises need to keep pace with the development. However, it is difficult to ensure system universality and stability because internal systems are dependent on each other. APIG uses standard RESTful APIs to simplify the service architecture, decouples internal systems, and separates the frontend from backend. Existing capabilities can be reused to avoid repetitive development.

|image1|

Enterprise Capabilities Opening
-------------------------------

An enterprise cannot develop without partners' capabilities, such as a third-party payment platform and partner account login. APIG enables you to selectively expose capabilities to partners by using standard APIs and share services and data with partners to build a new ecosystem.

|image2|

FunctionGraph Services Opening
------------------------------

APIG can also help you selectively expose serverless services (FunctionGraph services) to partners. FunctionGraph services are easier to develop, deploy, and maintain than traditional services. You can use FunctionGraph to quickly build backend service logic, and use APIG to expose service logic functions for linear concurrency expansion.

|image3|

.. |image1| image:: /_static/images/en-us_image_0168722756.png
.. |image2| image:: /_static/images/en-us_image_0168722761.png
.. |image3| image:: /_static/images/en-us_image_0168722767.png
