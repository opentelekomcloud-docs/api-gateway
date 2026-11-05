:original_name: apig_03_0015.html

.. _apig_03_0015:

Exporting APIs
==============

APIG allows you to export created APIs in the format defined by the OAS standard for scenarios such as migration, backup, and sharing.

Constraints
-----------

-  Constraints on APIG parameters:

   -  APIG does not support the configuration of request parameters in the **formData** and **body** locations.
   -  APIG does not support the configuration of parameters **consumes** and **produces**.
   -  The names of header parameters are case-insensitive.

-  Constraints on backend policies:

   -  When the backend type is **HTTP**, both HTTP and HTTP-VPC backends are supported.
   -  When the backend type is **HTTP-VPC**, both HTTP and HTTP-VPC backends are supported.
   -  When the backend type is **function**, only function backends are supported.
   -  When the backend type is **mock**, only mock backends are supported.

-  Among the APIs with the same path but different matching modes, the ones with prefix match have a path suffixed by the **default_swa_path** variable.
-  Currently, only the frontend and backend configurations of APIs can be exported.
-  gRPC APIs cannot be exported.


Exporting APIs
--------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Groups**. Click a group name and click **Export**.

   Or choose **API Management** > **APIs**, and click **Export APIs**.

4. Set the parameters according to the following table.

   .. table:: **Table 1** Parameters for exporting APIs

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================================================================================================+
      | API Group                         | Select the group of which APIs will be exported.                                                                                                                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Environment                       | Select the environment where the APIs to be exported have been published.                                                                                                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | APIs                              | By default, all APIs in the group that have been published in the selected environment are exported. To export only specific APIs, click **Select APIs**, and specify the APIs you want to export.                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | API Definition                    | API definition to be exported. Options:                                                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                                                               |
      |                                   | -  **Full**: The full definition of an API is composed of the request, backend, and response definitions. This function can be used to back up the full definition of an API as a Swagger or OpenAPI file.                                                                                    |
      |                                   | -  **Extended**: The extended definition of an API is composed of the request, backend, and response definitions as well as the request throttling policy, access control policy, and plug-in policies and their binding relationships with APIs.                                             |
      |                                   | -  **Basic**: The basic definition of an API is composed of the request and response definitions. It does not include the backend definition. The request definition includes both standard and extended Swagger fields. This function can generate a Swagger or OpenAPI API definition file. |
      |                                   | -  **Development**: **Full** plus frontend and backend definitions of APIs that are not published.                                                                                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Format                            | Select **JSON**, **YAML**, or **YML**.                                                                                                                                                                                                                                                        |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Version                           | Set the version of the APIs to be exported. If you do not specify a version, the version will be set as the current date and time.                                                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | OpenAPI Version                   | Export Swagger 2.0 or OpenAPI 3.0 APIs.                                                                                                                                                                                                                                                       |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

5. Click **Export**. The export result is displayed on the right of the page and the API file is automatically downloaded.
