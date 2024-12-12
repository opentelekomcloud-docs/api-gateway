:original_name: apig_03_0028.html

.. _apig_03_0028:

Signature Keys
==============

Signature keys are used by backend services to verify the identity of APIG.

A signature key consists of a key and secret, and can be used only after being bound to an API. When an API bound with a signature key is called, APIG adds signature details to the API request. The backend service of the API signs the request in the same way, and verifies the identity of APIG by checking whether the signature is consistent with that in the **Authorization** header sent by APIG.

Usage Guidelines
----------------

-  You have understood the :ref:`guidelines for policy creation and API binding <apig_03_0019__en-us_topic_0000001221774151_en-us_topic_0000001151883501_section126118109015>`.
-  An API can only be bound with one signature key in a given environment, but each signature key can be bound to multiple APIs.

Procedure
---------


.. figure:: /_static/images/en-us_image_0000001228425421.png
   :alt: **Figure 1** Signature key process flow

   **Figure 1** Signature key process flow

#. Create a signature key on the APIG console.
#. Bind the signature key to an API.
#. APIG sends signed requests containing a signature in the **Authorization** header to the backend service. The backend service can use different programming languages (Java, Go, Python, JavaScript, C#, PHP, C++, and C) to sign each request, and check whether the two signatures are consistent.

Configuration Parameters
------------------------

.. table:: **Table 1** Configuration parameters

   +-----------------------------------+-------------------------------------------------------------------------------------------+
   | Parameter                         | Description                                                                               |
   +===================================+===========================================================================================+
   | Name                              | Signature key name.                                                                       |
   +-----------------------------------+-------------------------------------------------------------------------------------------+
   | Type                              | Authentication type. Options: **HMAC**, **Basic auth**, **AES**.                          |
   +-----------------------------------+-------------------------------------------------------------------------------------------+
   | Signature Algorithm               | Select an AES signature algorithm. Options:                                               |
   |                                   |                                                                                           |
   |                                   | -  aes-128-cfb                                                                            |
   |                                   | -  aes-256-cfb                                                                            |
   +-----------------------------------+-------------------------------------------------------------------------------------------+
   | Key                               | Set the key based on the signature key type you have selected.                            |
   |                                   |                                                                                           |
   |                                   | -  If **Type** is **HMAC**, enter the key of the key pair used for app authentication.    |
   |                                   | -  If **Type** is **Basic auth**, enter the username used for basic authentication.       |
   |                                   | -  If **Type** is set to **AES**, enter the key used for AES authentication.              |
   +-----------------------------------+-------------------------------------------------------------------------------------------+
   | Secret                            | Enter the secret information based on the key type you have selected.                     |
   |                                   |                                                                                           |
   |                                   | -  If **Type** is **HMAC**, enter the secret of the key pair used for app authentication. |
   |                                   | -  If **Type** is **Basic auth**, enter the password used for basic authentication.       |
   |                                   | -  If **Type** is set to **AES**, enter the vector used for AES authentication.           |
   +-----------------------------------+-------------------------------------------------------------------------------------------+
   | Confirm Secret                    | Enter the secret again.                                                                   |
   +-----------------------------------+-------------------------------------------------------------------------------------------+

Verifying the Signing Result
----------------------------

Sign each backend request by following the instructions in section "Creating Signatures for Backend Requests" in the *API Gateway Developer Guide*, and check whether the backend signature is consistent with the signature in the **Authorization** header of the API request.
