:original_name: apig-en-ug-180307041.html

.. _apig-en-ug-180307041:

Creating and Using a Signature Key
==================================

Scenario
--------

Signature keys are used by backend services to verify the identity of APIG.

A signature key consists of a key and secret, and can be used only after being bound to an API. When an API bound with a signature key is called, APIG adds signature details to the API request. The backend service of the API signs the request in the same way, and verifies the identity of APIG by checking whether the signature is consistent with that in the **Authorization** header sent by APIG.

.. note::

   Each API can only be bound with one signature key in a given environment, but each signature key can be bound to multiple APIs.

Procedure
---------

#. Create a signature key on the APIG console.
#. Bind the signature key to an API.
#. APIG sends signed requests containing a signature in the **Authorization** header to the backend service. The backend service can use different programming languages (such as Java, Go, Python, JavaScript, C#, PHP, C++, C, and Android) to sign each request, and check whether the two signatures are consistent.


.. figure:: /_static/images/en-us_image_0000001142757900.png
   :alt: **Figure 1** Signature key process flow

   **Figure 1** Signature key process flow

Creating a Signature Key
------------------------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **Signature Keys**.

#. Click **Create Signature Key**.

#. In the **Create Signature Key** dialog box, set the parameters listed in :ref:`Table 1 <apig-en-ug-180307041__table1983417509557>`.

   .. _apig-en-ug-180307041__table1983417509557:

   .. table:: **Table 1** Parameters for creating a signature key

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                              |
      +===================================+==========================================================================================================================================+
      | Name                              | Signature key name.                                                                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Type of the signature key. Select **HMAC** or **Basic**. This parameter is available only for dedicated gateways.                        |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
      | Key                               | Combined with **Secret** to form a signature key pair.                                                                                   |
      |                                   |                                                                                                                                          |
      |                                   | -  If you set **Type** to **HMAC**, enter the key of the key pair used for hash-based message authentication code (HMAC) authentication. |
      |                                   | -  If you set **Type** to **Basic**, enter the username used for basic authentication.                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
      | Secret                            | Combined with **Key** to form a signature key pair.                                                                                      |
      |                                   |                                                                                                                                          |
      |                                   | -  If you set **Type** to **HMAC**, enter the secret of the key pair used for HMAC authentication.                                       |
      |                                   | -  If you set **Type** to **Basic**, enter the password used for basic authentication.                                                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Secret                    | Enter the secret again.                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

Binding a Signature Key to an API
---------------------------------

#. In the navigation pane, choose **API Publishing** > **Signature Keys**.
#. Bind a signature key to an API. You can use one of the following methods:

   -  In the **Operation** column of the signature key to be bound to an API, click **Bind to API**.
   -  Click the name of the target signature key.

#. Click **Select API**.
#. Specify an API group, environment, and API name keyword to search for the desired API.
#. Select the API and click **OK**.

   .. note::

      If a signature key is no longer needed for an API, unbind it from the API.

Verifying the Signing Result
----------------------------

Sign each backend request by following the instructions in section "Creating Signatures for Backend Requests" of the *API Gateway Developer Guide*, and check whether the backend signature is consistent with the signature in the **Authorization** header of the API request.
