:original_name: apig_03_0057.html

.. _apig_03_0057:

API Authorization Overview
==========================

When calling an API that uses App authentication, API callers can use credentials or AppCodes for simple API authentication. The following table lists the app authentication types. For more information, see :ref:`Calling an Open API <apig_03_0046>`.

.. table:: **Table 1** App authentication types

   +---------------------------+------------------------------------------------------------+
   | Type                      | Authentication Mode                                        |
   +===========================+============================================================+
   | Signature authentication  | Credential                                                 |
   +---------------------------+------------------------------------------------------------+
   | Simple authentication     | AppCode                                                    |
   +---------------------------+------------------------------------------------------------+
   | Two-way authentication    | Credential and :ref:`custom authentication <apig_03_0029>` |
   +---------------------------+------------------------------------------------------------+
   | app_secret authentication | Credential                                                 |
   +---------------------------+------------------------------------------------------------+
   | app_basic authentication  | Credential                                                 |
   +---------------------------+------------------------------------------------------------+

-  :ref:`Configuring Authentication Credentials <apig_03_0056>`

   Create a credential to generate a key/secret pair. When an API is called, APIG authenticates the identity based on the key/secret pair. The key is unique and cannot be reset. The secret can be :ref:`reset <apig_03_0056__section19872617202717>`.

-  :ref:`Configuring AppCodes for Simple Authentication <apig_03_0058>`

   After the simple authentication is configured, APIG can perform authentication based on the AppCode or key/secret pair when calling the API.
