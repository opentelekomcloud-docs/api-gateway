:original_name: apig-faq-190627027.html

.. _apig-faq-190627027:

Why Does an API Failed to Be Called Across Domains?
===================================================

#. Ensure that CORS has been enabled for the API.

   Go to the API details page, click **Edit**, and check whether CORS is enabled. If it is not, enable it.

#. Check whether an API with the OPTIONS method has been created. Only one such API is required for each API group.

   a. On the **Set Basic Information** page, set the basic information for the API that uses the OPTIONS method.

      Go to the API details page and click **Edit**.

      **API Group**: The group to which the API with CORS enabled belongs.

      **Security Authentication**: **None** means all users will be granted access. It is not recommended.

   b. On the **Define API Request** page, set the request information for the API.

      -  **Protocol**: The same protocol used by the API with CORS enabled.
      -  **Path**: Same as or prefixally matching the request path set for the API with CORS enabled.
      -  **Matching**: Select **Prefix match**.
      -  **Method**: Select **OPTIONS**.
      -  **CORS**: Enable this option.
