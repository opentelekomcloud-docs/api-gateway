:original_name: apig-faq-190627027.html

.. _apig-faq-190627027:

Why Does an API Failed to Be Called Across Domains?
===================================================

#. Ensure that CORS has been enabled for the API.

   Go to the API details page, click **Edit**, and check whether CORS is enabled. If it is not, enable it.

#. Check whether an API with the OPTIONS method has been created. Only one such API is required for each API group.

   .. note::

      Parameters are as follows:

      **API Group**: The same group to which the API with CORS enabled belongs.

      **Method**: Select **OPTIONS**.

      **Protocol**: The same protocol used by the API with CORS enabled.

      **Path**: Same as or prefixally matching the request path set for the API with CORS enabled.

      **Matching**: Select **Prefix match**.

      **Authentication Mode**: **None** means all users will be granted access. It is not recommended.

      **CORS**: Enable this option.
