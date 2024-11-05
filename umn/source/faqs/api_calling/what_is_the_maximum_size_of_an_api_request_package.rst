:original_name: apig-faq-180606013.html

.. _apig-faq-180606013:

What Is the Maximum Size of an API Request Package?
===================================================

Dedicated gateway: APIG forwards only API requests whose body is no larger than 12 MB. If your gateway will receive requests with a body larger than 12 MB, modify the **request_body_size** parameter on the gateway details page. This parameter indicates the maximum request body size allowed. The value ranges from 1 MB to 9536 MB.
