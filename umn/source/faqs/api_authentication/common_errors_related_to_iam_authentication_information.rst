:original_name: apig-faq-0003.html

.. _apig-faq-0003:

Common Errors Related to IAM Authentication Information
=======================================================

You may encounter the following errors related to IAM authentication information:

-  :ref:`Incorrect IAM authentication information: AK access failed to reach the limit,forbidden <apig-faq-0003__en-us_topic_0000001212792613_en-us_topic_0000001128323062_section1869305817620>`
-  :ref:`Incorrect IAM authentication information: decrypt token fail <apig-faq-0003__en-us_topic_0000001212792613_en-us_topic_0000001128323062_section20529131916177>`
-  :ref:`Incorrect IAM authentication information: Get secretKey failed <apig-faq-0003__en-us_topic_0000001212792613_en-us_topic_0000001128323062_section14399016152116>`

.. _apig-faq-0003__en-us_topic_0000001212792613_en-us_topic_0000001128323062_section1869305817620:

Incorrect IAM authentication information: AK access failed to reach the limit,forbidden
---------------------------------------------------------------------------------------

.. code-block::

   {
     "error_msg": "Incorrect IAM authentication information: AK access failed to reach the limit,forbidden." ......
     "error_code": "APIG.0301",
     "request_id": "******"
   }

**Possible Causes**

-  The AK/SK signature calculation is incorrect.
-  The AK and SK do not match.
-  AK/SK authentication fails for more than five consecutive times, and the AK/SK pair is locked for five minutes. (Authentication requests are rejected within this period).
-  An expired token is used for token authentication.

.. _apig-faq-0003__en-us_topic_0000001212792613_en-us_topic_0000001128323062_section20529131916177:

Incorrect IAM authentication information: decrypt token fail
------------------------------------------------------------

.. code-block::

   {
     "error_msg": "Incorrect IAM authentication information: decrypt token fail",
     "error_code": "APIG.0301",
     "request_id": "******"
   }

**Possible Cause**

The token cannot be parsed for IAM authentication of the API.

**Solution**

-  Check whether the obtained token is the token of the corresponding IAM account.
-  Check whether the token is correct.
-  Check whether the token has been obtained in the environment where the API is called.

.. _apig-faq-0003__en-us_topic_0000001212792613_en-us_topic_0000001128323062_section14399016152116:

Incorrect IAM authentication information: Get secretKey failed
--------------------------------------------------------------

.. code-block::

   {
   "error_msg": "Incorrect IAM authentication information: Get secretKey failed,ak:******,err:ak not exist",
   "error_code": "APIG.0301",
   "request_id": "******"
   }

**Possible Cause**

The AK used for IAM authentication of the API does not exist.

**Solution**

Check whether the AK is correct.
