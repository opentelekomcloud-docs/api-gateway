:original_name: apig-faq-0003.html

.. _apig-faq-0003:

Common Errors Related to IAM Authentication Information
=======================================================

You may encounter the following errors related to IAM authentication information:

-  :ref:`Incorrect IAM authentication information: verify aksk signature fail <apig-faq-0003__en-us_topic_0000001128323062_section18226134155618>`
-  :ref:`Incorrect IAM authentication information: AK access failed to reach the limit,forbidden <apig-faq-0003__en-us_topic_0000001128323062_section1869305817620>`
-  :ref:`Incorrect IAM authentication information: decrypt token fail <apig-faq-0003__en-us_topic_0000001128323062_section20529131916177>`
-  :ref:`Incorrect IAM authentication information: Get secretKey failed <apig-faq-0003__en-us_topic_0000001128323062_section14399016152116>`

.. _apig-faq-0003__en-us_topic_0000001128323062_section18226134155618:

Incorrect IAM authentication information: verify aksk signature fail
--------------------------------------------------------------------

.. code-block::

   {
     "error_msg": "Incorrect IAM authentication information: verify aksk signature fail, ......
     "error_code": "APIG.0301",
     "request_id": "******"
   }

**Possible Cause**

The signature algorithm is incorrect, and the signature calculated by the client is different from that calculated by APIG.

**Solution**

#. .. _apig-faq-0003__en-us_topic_0000001128323062_li457620321347:

   Obtain the canonicalRequest calculated by APIG.

   Obtain **request_id** from the body of the error message, search for **error.log** (you can view this file on CLS) of the shubao node based on **request_id**, and obtain **canonicalRequest** from **error.log**.

   .. code-block::

      2019/01/26 11:34:27 [error] 1211#0: *76 [lua] responses.lua:170: rewrite(): 473a4370fbaf69e42f9da243eb8f8c52;app-1;Incorrect IAM authentication information: verify signature fail;SDK-HMAC-SHA256 Access=071fe245-9cf6-4d75-822d-c29945a1e06a, SignedHeaders=host;x-sdk-date, Signature=b2ef2cddcef89cbfe22974c988909c1a94b1ac54114c30b8fe083d34a259e0f5;canonicalRequest:GET
      /app1/

      host:test.com
      x-sdk-date:20190126T033427Z

      host;x-sdk-date
      e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855, client: 192.168.0.1, server: shubao, request: "GET /app1 HTTP/1.1", host: "test.com"

#. .. _apig-faq-0003__en-us_topic_0000001128323062_li13153173174014:

   Obtain the canonicalRequest calculated by the client by printing logs or using debug interrupts. The following table describes the functions used to calculate the canonicalRequest in the SDKs of different languages.

   .. table:: **Table 1** Functions for calculating canonicalRequest in the SDKs of common languages

      +------------+------------------------------------------------------------------------------------------------+
      | Language   | Function                                                                                       |
      +============+================================================================================================+
      | Java       | Sign function in com.cloud.sdk.auth.signer.DefaultSigner.class of **libs/java-sdk-core-*.jar** |
      +------------+------------------------------------------------------------------------------------------------+
      | C          | sig_sign function in **signer.c**                                                              |
      +------------+------------------------------------------------------------------------------------------------+
      | C++        | Signer::createSignature function in **signer.cpp**.                                            |
      +------------+------------------------------------------------------------------------------------------------+
      | C#         | Sign function in **signer.cs**                                                                 |
      +------------+------------------------------------------------------------------------------------------------+
      | Go         | Sign function in **signer.go**                                                                 |
      +------------+------------------------------------------------------------------------------------------------+
      | JavaScript | Signer.prototype.Sign function in **signer.js**                                                |
      +------------+------------------------------------------------------------------------------------------------+
      | Python     | Sign function in **signer.py**                                                                 |
      +------------+------------------------------------------------------------------------------------------------+
      | PHP        | Sign function in **signer.php**                                                                |
      +------------+------------------------------------------------------------------------------------------------+

   Example: cannonicalRequest obtained at a debug interrupt

   .. code-block:: text

      POST
      /app1/

      host:test.com
      x-sdk-date:20190126T033950Z

      host;x-sdk-date
      e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855

#. Check whether the cannonicalRequest in :ref:`1 <apig-faq-0003__en-us_topic_0000001128323062_li457620321347>` is the same as that in :ref:`2 <apig-faq-0003__en-us_topic_0000001128323062_li13153173174014>`.

   -  Yes: Check whether the AK and SK are correct, for example, without spaces.
   -  No:

      -  Different in line 1: The request method must be the same.
      -  Different in line 2: The request path must be the same.
      -  Different in line 3: The request parameters must be the same.
      -  Different in lines 4 to 5: The request header must be the same in each line.
      -  Different in line 7: The number of request header parameters must be the same as the number of request header lines.
      -  Different in line 8: The request body must be the same.

   .. table:: **Table 2** canonicalRequest of APIG and a client

      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | Line No. | Parameter                 | APIG                                                             | Client                                                           |
      +==========+===========================+==================================================================+==================================================================+
      | 1        | Request method            | GET                                                              | POST                                                             |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 2        | Request path              | /app1/                                                           | /app1/                                                           |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 3        | Request parameters        | None                                                             | None                                                             |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 4        | Request header            | host:test.com                                                    | host:test.com                                                    |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 5        | Request header            | x-sdk-date:20190126T033427Z                                      | x-sdk-date:20190126T033950Z                                      |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 6        | Blank line                | ``-``                                                            | ``-``                                                            |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 7        | Request header parameters | host;x-sdk-date                                                  | host;x-sdk-date                                                  |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+
      | 8        | Request body hash value   | e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 | e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 |
      +----------+---------------------------+------------------------------------------------------------------+------------------------------------------------------------------+

.. _apig-faq-0003__en-us_topic_0000001128323062_section1869305817620:

Incorrect IAM authentication information: AK access failed to reach the limit,forbidden
---------------------------------------------------------------------------------------

.. code-block::

   {
     "error_msg": "Incorrect IAM authentication information: AK access failed to reach the limit,forbidden." ......
     "error_code": "APIG.0301",
     "request_id": "******"
   }

**Possible Causes**

-  The AK/SK signature calculation is incorrect. Resolve the problem by referring to :ref:`Incorrect IAM authentication information: verify aksk signature fail <apig-faq-0003__en-us_topic_0000001128323062_section18226134155618>`.
-  The AK and SK do not match.
-  AK/SK authentication fails for more than five consecutive times, and the AK/SK pair is locked for five minutes. (Authentication requests are rejected within this period).
-  An expired token is used for token authentication.

.. _apig-faq-0003__en-us_topic_0000001128323062_section20529131916177:

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

-  Check whether the token is correct.
-  Check whether the token has been obtained in the environment where the API is called.

.. _apig-faq-0003__en-us_topic_0000001128323062_section14399016152116:

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
