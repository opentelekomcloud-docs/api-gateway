:original_name: apig-en-ug-181204105.html

.. _apig-en-ug-181204105:

Exporting APIs
==============

Scenario
--------

You can export APIs one by one or in batches as JSON or YAML files.

Prerequisites
-------------

You have created an API group and API.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. Click **Export API**.

#. Set the parameters listed in :ref:`Table 1 <apig-en-ug-181204105__en-us_topic_0142347425_table11284181112369>`.

   .. _apig-en-ug-181204105__en-us_topic_0142347425_table11284181112369:

   .. table:: **Table 1** Parameters for exporting APIs

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================================================+
      | API Group                         | Select the API group from which APIs will be exported.                                                                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment                       | Select the environment where the APIs to be exported have been published.                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | APIs                              | By default, all APIs in the API group that have been published in the selected environment are exported. To export only specific APIs, click **Select API**, and specify the APIs you want to export.                    |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Definition                    | -  **Basic**: The basic definition of an API is composed of the request and response definitions. It does not include the backend definition. The request definition includes both standard and extended Swagger fields. |
      |                                   | -  **Full**: The full definition of an API is composed of the request, backend, and response definitions.                                                                                                                |
      |                                   | -  **Extended**: The extended definition of an API is composed of the request, backend, and response definitions as well as the request throttling policy, access control policy, and other configurations of the API.   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Format                            | Export APIs in **JSON** or **YAML** format.                                                                                                                                                                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Version                           | Set the version of the APIs to be exported. If you do not specify a version, the version will be set as the current date and time.                                                                                       |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Export**.

   The export result is displayed on the right.
