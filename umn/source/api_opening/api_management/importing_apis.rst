:original_name: apig-en-ug-181025104.html

.. _apig-en-ug-181025104:

Importing APIs
==============

Scenario
--------

APIG allows you to import Swagger 2.0 APIs to existing or new API groups. Swagger is an open-source tool built based on OpenAPI specifications to design, build, record, and use REST APIs.

You can import APIs individually or in batches depending on the number of APIs contained in a Swagger file.

Prerequisites
-------------

-  Supplement the extended Swagger definition of the APIs to import. If the extended definition does not contain the required settings, create them on the APIG console.
-  You have sufficient API group and API quotas.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. In the navigation pane, choose **API Publishing** > **APIs**.

#. Click **Import API**.

#. Set the parameters listed in :ref:`Table 1 <apig-en-ug-181025104__en-us_topic_0137035339_table11284181112369>`.

   .. _apig-en-ug-181025104__en-us_topic_0137035339_table11284181112369:

   .. table:: **Table 1** Parameters for importing APIs

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                    |
      +===================================+================================================================================================================================================================================================+
      | Import                            | Options:                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                |
      |                                   | -  **New group**: Import APIs to a new API group. If you select this option, the system automatically creates an API group and imports the APIs into this group.                               |
      |                                   | -  **Existing group**: Import APIs to an existing API group. If you select this option, the system adds the APIs to the selected API group while retaining the existing APIs in the API group. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API group                         | Select an API group if you set **Import** to **Existing group**.                                                                                                                               |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Basic Definition Overwrite        | Determine whether to overwrite an existing API if the name of the API is the same as that of an imported API.                                                                                  |
      |                                   |                                                                                                                                                                                                |
      |                                   | This parameter is available only if you set **Import** to **Existing group**.                                                                                                                  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Extended Definition Overwrite     | If this option is selected, the extended definition items (access control and request throttling policies) of an imported API will overwrite the existing policies with the same name.         |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. In the **Parameter Import** area, click **File** and select a file to import.

   YAML and JSON files are supported. You can preview the API content to be imported on the **Import API** page.

#. (Optional) Configure global settings for the APIs to be imported.

   You can configure the global settings for the APIs, such as frontend and backend requests, or modify other parameters of the APIs.

#. Click **Import Now** to import the APIs.

   .. note::

      Imported APIs must be manually published so that they become available for users to access.

Follow-Up Operations
--------------------

:ref:`Publish <apig-en-ug-180307023>` the imported API in an environment so that it can be called by users.
