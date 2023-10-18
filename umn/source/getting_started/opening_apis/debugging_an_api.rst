:original_name: apig-ug-190419108.html

.. _apig-ug-190419108:

Debugging an API
================

#. On the **APIs** page, locate the API created in :ref:`Creating an API <en-us_topic_0080101678>`, and choose **More** > **Debug**.

#. On the left side, set the API request parameters listed in :ref:`Table 1 <apig-ug-190419108__en-us_topic_0165548134_en-us_topic_0080103327_table1699044810457>`. On the right side, view the API request and response information after you click **Send Request**.

   .. _apig-ug-190419108__en-us_topic_0165548134_en-us_topic_0080103327_table1699044810457:

   .. table:: **Table 1** Parameters for debugging an API

      +---------------+-----------------------------------------------------------------------------------------------------------+
      | Parameter     | Description                                                                                               |
      +===============+===========================================================================================================+
      | Protocol      | This parameter can be modified only if you set **Protocol** to **HTTP&HTTPS** for the API.                |
      +---------------+-----------------------------------------------------------------------------------------------------------+
      | Method        | This parameter can be modified only if you set **Method** to **ANY** for the API.                         |
      +---------------+-----------------------------------------------------------------------------------------------------------+
      | Path          | Request path of the API.                                                                                  |
      +---------------+-----------------------------------------------------------------------------------------------------------+
      | Query Strings | Query string parameters and values.                                                                       |
      +---------------+-----------------------------------------------------------------------------------------------------------+
      | Headers       | HTTP headers and values.                                                                                  |
      +---------------+-----------------------------------------------------------------------------------------------------------+
      | Body          | This parameter can be modified only if you set **Method** to **PATCH**, **POST**, or **PUT** for the API. |
      +---------------+-----------------------------------------------------------------------------------------------------------+

#. Click **Send Request**.

   If the API is called successfully, the status code **200** is displayed.
