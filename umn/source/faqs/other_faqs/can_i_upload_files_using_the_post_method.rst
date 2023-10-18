:original_name: apig-en-faq-180307006.html

.. _apig-en-faq-180307006:

Can I Upload Files Using the POST Method?
=========================================

Yes.

If you are using dedicated gateways, configure the maximum request body size allowed by setting the **request_body_size** parameter. The value ranges from 1 MB to 9536 MB.

.. note::

   Currently, only the request body can be transparently transmitted.
