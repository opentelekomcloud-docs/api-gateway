:original_name: UpdatePlugin.html

.. _UpdatePlugin:

Modifying a Plug-in
===================

Function
--------

This API is used to modify a plug-in.

-  Plug-in names must be unique.

-  The plug-in type and scope cannot be modified.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

PUT /v2/{project_id}/apigw/instances/{instance_id}/plugins/{plugin_id}

.. table:: **Table 1** Path Parameters

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                             |
   +=============+===========+========+=========================================================================================================+
   | project_id  | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Gateway ID, which can be obtained from the gateway information on the APIG console.                     |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | plugin_id   | Yes       | String | Plug-in ID.                                                                                             |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                             |
   +=================+=================+=================+=========================================================================================================================+
   | plugin_name     | Yes             | String          | Plug-in name. Enter 3 to 255 characters, starting with a letter. Only letters, digits, and underscores (_) are allowed. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | plugin_type     | Yes             | String          | Plug-in type.                                                                                                           |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  cors: Cross-origin resource sharing.                                                                                 |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  set_resp_headers: HTTP response header management.                                                                   |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  kafka_log: Kafka log push.                                                                                           |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  breaker: Circuit breaker.                                                                                            |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  rate_limit: Request throttling.                                                                                      |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  third_auth: Third-party authentication.                                                                              |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | Enumeration values:                                                                                                     |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **cors**                                                                                                             |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **set_resp_headers**                                                                                                 |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **kafka_log**                                                                                                        |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **breaker**                                                                                                          |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **rate_limit**                                                                                                       |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **third_auth**                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | plugin_scope    | Yes             | String          | Plug-in scope. global: Visible to all gateways.                                                                         |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | Enumeration values:                                                                                                     |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  **global**                                                                                                           |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | plugin_content  | Yes             | String          | Plug-in content in JSON format. For details, see the model definition.                                                  |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  CorsPluginContent                                                                                                    |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  SetRespHeadersContent                                                                                                |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  KafkaLogContent                                                                                                      |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  BreakerContent                                                                                                       |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  RateLimitContent                                                                                                     |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | -  ThirdAuthContent                                                                                                     |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | Maximum: **65535**                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | remark          | No              | String          | Plug-in description, with a maximum of 255 characters.                                                                  |
   |                 |                 |                 |                                                                                                                         |
   |                 |                 |                 | Maximum: **255**                                                                                                        |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                 |
   +=======================+=======================+=============================================================================================================================+
   | plugin_id             | String                | Plug-in ID.                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_name           | String                | Plug-in name. Start with a letter, and include only letters, digits, hyphens (-), and underscores(_). (3 to 255 characters) |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_type           | String                | Plug-in type.                                                                                                               |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  cors: Cross-origin resource sharing.                                                                                     |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  set_resp_headers: HTTP response header management.                                                                       |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  kafka_log: Kafka log push.                                                                                               |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  breaker: Circuit breaker.                                                                                                |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  rate_limit: Request throttling.                                                                                          |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  third_auth: Third-party authentication.                                                                                  |
   |                       |                       |                                                                                                                             |
   |                       |                       | Enumeration values:                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **cors**                                                                                                                 |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **set_resp_headers**                                                                                                     |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **kafka_log**                                                                                                            |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **breaker**                                                                                                              |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **rate_limit**                                                                                                           |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **third_auth**                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_scope          | String                | Plug-in scope. global: Visible to all gateways.                                                                             |
   |                       |                       |                                                                                                                             |
   |                       |                       | Enumeration values:                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  **global**                                                                                                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | plugin_content        | String                | Plug-in content in JSON format. For details, see the model definition.                                                      |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  CorsPluginContent                                                                                                        |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  SetRespHeadersContent                                                                                                    |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  KafkaLogContent                                                                                                          |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  BreakerContent                                                                                                           |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  RateLimitContent                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | -  ThirdAuthContent                                                                                                         |
   |                       |                       |                                                                                                                             |
   |                       |                       | Maximum: **65535**                                                                                                          |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | remark                | String                | Plug-in description, with a maximum of 255 characters.                                                                      |
   |                       |                       |                                                                                                                             |
   |                       |                       | Maximum: **255**                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                | Creation time.                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+
   | update_time           | String                | Update time.                                                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 404**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

Example Requests
----------------

-  Updating a CORS plug-in

   .. code-block::

      {
        "plugin_name" : "CORS",
        "plugin_type" : "cors",
        "plugin_scope" : "global",
        "plugin_content" : "{\"allow_origin\": \"*\",\"allow_methods\": \"GET,POST,PUT\",\"allow_headers\": \"Content-Type,Accept,Accept-Ranges,Cache-Control\",\"expose_headers\": \"X-Request-Id,X-Apig-Latency\",\"max_age\": 172800,\"allow_credentials\": true}",
        "remark" : "Cross-origin resource sharing"
      }

-  Updating an HTTP response header plug-in

   .. code-block::

      {
        "plugin_name" : "HTTP Response Header Plug-in",
        "plugin_type" : "set_resp_headers",
        "plugin_scope" : "global",
        "plugin_content" : "{\\\"response_headers\\\":[{\\\"name\\\":\\\"x-demo\\\",\\\"value\\\":\\\"sss\\\",\\\"action\\\":\\\"append\\\"}]}",
        "remark" : "HTTP response header management"
      }

-  Updating a request throttling plug-in

   .. code-block::

      {
        "plugin_name" : "Request Throttling Plug-in",
        "plugin_type" : "rate_limit",
        "plugin_scope" : "global",
        "plugin_content" : "{\\\"scope\\\":\\\"basic\\\",\\\"default_time_unit\\\":\\\"minute\\\",\\\"default_interval\\\":1,\\\"api_limit\\\":50,\\\"app_limit\\\":0,\\\"user_limit\\\":0,\\\"ip_limit\\\":0,\\\"algorithm\\\":\\\"counter\\\",\\\"specials\\\":[],\\\"parameters\\\":[],\\\"rules\\\":[]}",
        "remark" : "Request throttling"
      }

-  Updating a Kafka log push plug-in

   .. code-block::

      {
        "plugin_name" : "Kafka Log Plug-in",
        "plugin_type" : "kafka_log",
        "plugin_scope" : "app",
        "plugin_content" : "{\\\"broker_list\\\":[\\\"0.0.0.0:11\\\"],\\\"topic\\\":\\\"topic\\\",\\\"key\\\":\\\"\\\",\\\"max_retry_count\\\":0,\\\"retry_backoff\\\":1,\\\"sasl_config\\\":{\\\"security_protocol\\\":\\\"PLAINTEXT\\\",\\\"sasl_mechanisms\\\":\\\"PLAIN\\\",\\\"sasl_username\\\":\\\"\\\",\\\"sasl_password\\\":\\\"\\\",\\\"ssl_ca_content\\\":\\\"\\\"},\\\"meta_config\\\":{\\\"system\\\":{\\\"start_time\\\":true,\\\"request_id\\\":true,\\\"client_ip\\\":true,\\\"api_id\\\":false,\\\"user_name\\\":false,\\\"app_id\\\":false,\\\"access_model1\\\":false,\\\"request_time\\\":true,\\\"http_status\\\":true,\\\"server_protocol\\\":false,\\\"scheme\\\":true,\\\"request_method\\\":true,\\\"host\\\":false,\\\"api_uri_mode\\\":false,\\\"uri\\\":false,\\\"request_size\\\":false,\\\"response_size\\\":false,\\\"upstream_uri\\\":false,\\\"upstream_addr\\\":true,\\\"upstream_status\\\":true,\\\"upstream_connect_time\\\":false,\\\"upstream_header_time\\\":false,\\\"upstream_response_time\\\":true,\\\"all_upstream_response_time\\\":false,\\\"region_id\\\":false,\\\"auth_type\\\":false,\\\"http_x_forwarded_for\\\":true,\\\"http_user_agent\\\":true,\\\"error_type\\\":true,\\\"access_model2\\\":false,\\\"inner_time\\\":false,\\\"proxy_protocol_vni\\\":false,\\\"proxy_protocol_vpce_id\\\":false,\\\"proxy_protocol_addr\\\":false,\\\"body_bytes_sent\\\":false,\\\"api_name\\\":false,\\\"app_name\\\":false,\\\"provider_app_id\\\":false,\\\"provider_app_name\\\":false,\\\"custom_data_log01\\\":false,\\\"custom_data_log02\\\":false,\\\"custom_data_log03\\\":false,\\\"custom_data_log04\\\":false,\\\"custom_data_log05\\\":false,\\\"custom_data_log06\\\":false,\\\"custom_data_log07\\\":false,\\\"custom_data_log08\\\":false,\\\"custom_data_log09\\\":false,\\\"custom_data_log10\\\":false,\\\"response_source\\\":false},\\\"call_data\\\":{\\\"log_request_header\\\":false,\\\"request_header_filter\\\":\\\"\\\",\\\"log_request_query_string\\\":false,\\\"request_query_string_filter\\\":\\\"\\\",\\\"log_request_body\\\":false,\\\"log_response_header\\\":false,\\\"response_header_filter\\\":\\\"\\\",\\\"log_response_body\\\":false,\\\"custom_authorizer\\\":{\\\"frontend\\\":[],\\\"backend\\\":[]}}}}",
        "remark" : "Kafka log push"
      }

-  Updating a circuit breaker plug-in

   .. code-block::

      {
        "plugin_name" : "Circuit Breaker Plug-in",
        "plugin_type" : "breaker",
        "plugin_scope" : "app",
        "plugin_content" : "{\\\"breaker_condition\\\":{\\\"breaker_type\\\":\\\"timeout\\\",\\\"breaker_mode\\\":\\\"counter\\\",\\\"unhealthy_condition\\\":\\\"\\\",\\\"unhealthy_threshold\\\":30,\\\"min_call_threshold\\\":20,\\\"unhealthy_percentage\\\":51,\\\"time_window\\\":15,\\\"open_breaker_time\\\":15},\\\"downgrade_default\\\":null,\\\"downgrade_parameters\\\":null,\\\"downgrade_rules\\\":null,\\\"scope\\\":\\\"basic\\\"}",
        "remark" : "Circuit breaker"
      }

-  Updating a third-party authentication plug-in

   .. code-block::

      {
        "plugin_name" : "Third-Party Authentication Plug-in",
        "remark" : "This is a third-party authentication plug-in that contains a rule expression blacklist.",
        "plugin_type" : "third_auth",
        "plugin_scope" : "global",
        "plugin_content" : "{\\\"auth_request\\\":{\\\"method\\\":\\\"POST\\\",\\\"protocol\\\":\\\"HTTP\\\",\\\"url_domain\\\":\\\"xxx.xxx.xxx.xxx:1234\\\",\\\"timeout\\\":10,\\\"path\\\":\\\"/check\\\",\\\"vpc_channel_enabled\\\":false,\\\"vpc_channel_info\\\":{\\\"vpc_proxy_host\\\":\\\"abc.com\\\",\\\"vpc_id\\\":\\\"3c113f40a54a40369ceb1eb1409a32ee\\\"}},\\\"identities\\\":{\\\"headers\\\":[{\\\"name\\\":\\\"token\\\"}],\\\"query\\\":[{\\\"name\\\":\\\"user\\\"}]},\\\"carry_body\\\":{\\\"enabled\\\":true,\\\"max_body_size\\\":10000},\\\"carry_path_enabled\\\":false,\\\"return_resp_body_enabled\\\":true,\\\"carry_resp_headers\\\":[\\\"x-message-result\\\"],\\\"simple_auth_mode_enabled\\\":false,\\\"match_auth\\\":{\\\"key\\\":\\\"x-message-result\\\",\\\"value\\\":\\\"success\\\"},\\\"rule_enabled\\\":true,\\\"rule_type\\\":\\\"deny\\\",\\\"parameters\\\":[{\\\"value\\\":\\\"reqPath\\\",\\\"type\\\":\\\"path\\\",\\\"name\\\":\\\"reqPath\\\"},{\\\"value\\\":\\\"method\\\",\\\"type\\\":\\\"method\\\",\\\"name\\\":\\\"method\\\"},{\\\"value\\\":\\\"Host\\\",\\\"type\\\":\\\"header\\\",\\\"name\\\":\\\"Host\\\"}],\\\"rules\\\":[{\\\"match_regex\\\": \\\"[\\\\\\\"OR\\\\\\\", [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/xxl-job-admin/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/leave/infor/v1/addLeaveLnfor\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/v1/charge/home/modifyChargeSync\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/mweb/campaign/api/v1/getActivityConfig\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/mp/vehicle/owner/home\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/mweb/campaign/api/v1/getTime\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/c-showroom-service/v1/vehicleDetails/upload\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/operation-charging-bff/carOwnerRights/certificate/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/api/2c/v1/sales-bff/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/2c/v1/vehicleDetails/upload\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/operation-admin/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/settings/api/v1/receiveClk\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/vehicle/relative/yTSendVehicleControl.json\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/appoint/getAppointmentByTestDrive\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/callBackEvdPay\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/callBackEvdOrder\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/getUserToken\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/callBackEvdCoupon\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/task/busTriggerTaskEvent.json\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/datacenter-log-center/api/trackApi/commonAdd.json\\\\\\\"]]\\\", \\\"rule_name\\\": \\\"allow2\\\"}],\\\"custom_forbid_limit\\\":100,\\\"auth_downgrade_enabled\\\":false}"
      }

Example Responses
-----------------

**Status code: 200**

OK

-  Example 1

   .. code-block::

      {
        "plugin_id" : "5b729aa252764739b3s237ef0d66dc63",
        "plugin_name" : "CORS Plug-in",
        "plugin_type" : "cors",
        "plugin_scope" : "global",
        "plugin_content" : "{\"allow_origin\": \"*\",\"allow_methods\": \"GET,POST,PUT\",\"allow_headers\": \"Content-Type,Accept,Accept-Ranges,Cache-Control\",\"expose_headers\": \"X-Request-Id,X-Apig-Latency\",\"max_age\": 172800,\"allow_credentials\": true}",
        "remark" : "Cross-origin resource sharing",
        "create_time" : "2020-11-02T12:31:23.353Z",
        "update_time" : "2020-11-02T12:31:23.353Z"
      }

-  Example 2

   .. code-block::

      {
        "plugin_id" : "8a688dce7d0c45cf84edac3d7b071769",
        "plugin_name" : "HTTP Response Header Plug-in",
        "plugin_type" : "set_resp_headers",
        "plugin_scope" : "global",
        "plugin_content" : "{\\\"response_headers\\\":[{\\\"name\\\":\\\"x-demo\\\",\\\"value\\\":\\\"sss\\\",\\\"action\\\":\\\"append\\\"}]}",
        "remark" : "HTTP response header management",
        "create_time" : "2022-11-02T12:31:23.353Z",
        "update_time" : "2022-11-02T12:31:23.353Z"
      }

-  Example 3

   .. code-block::

      {
        "plugin_id" : "9642ff2b9a86481689ca9d28babcfd7f",
        "plugin_name" : "Request Throttling Plug-in",
        "plugin_type" : "rate_limit",
        "plugin_scope" : "global",
        "plugin_content" : "{\\\"scope\\\":\\\"basic\\\",\\\"default_time_unit\\\":\\\"minute\\\",\\\"default_interval\\\":1,\\\"api_limit\\\":50,\\\"app_limit\\\":0,\\\"user_limit\\\":0,\\\"ip_limit\\\":0,\\\"algorithm\\\":\\\"counter\\\",\\\"specials\\\":[],\\\"parameters\\\":[],\\\"rules\\\":[]}",
        "remark" : "Request throttling",
        "create_time" : "2022-11-02T12:31:23.353Z",
        "update_time" : "2022-11-02T12:31:23.353Z"
      }

-  Example 4

   .. code-block::

      {
        "plugin_id" : "92284ece6ec7466da2c2ac2416f46d5d",
        "plugin_name" : "Kafka Log Plug-in",
        "plugin_type" : "kafka_log",
        "plugin_scope" : "app",
        "plugin_content" : "{\\\"broker_list\\\":[\\\"0.0.0.0:11\\\"],\\\"topic\\\":\\\"topic\\\",\\\"key\\\":\\\"\\\",\\\"max_retry_count\\\":0,\\\"retry_backoff\\\":1,\\\"sasl_config\\\":{\\\"security_protocol\\\":\\\"PLAINTEXT\\\",\\\"sasl_mechanisms\\\":\\\"PLAIN\\\",\\\"sasl_username\\\":\\\"\\\",\\\"sasl_password\\\":\\\"\\\",\\\"ssl_ca_content\\\":\\\"\\\"},\\\"meta_config\\\":{\\\"system\\\":{\\\"start_time\\\":true,\\\"request_id\\\":true,\\\"client_ip\\\":true,\\\"api_id\\\":false,\\\"user_name\\\":false,\\\"app_id\\\":false,\\\"access_model1\\\":false,\\\"request_time\\\":true,\\\"http_status\\\":true,\\\"server_protocol\\\":false,\\\"scheme\\\":true,\\\"request_method\\\":true,\\\"host\\\":false,\\\"api_uri_mode\\\":false,\\\"uri\\\":false,\\\"request_size\\\":false,\\\"response_size\\\":false,\\\"upstream_uri\\\":false,\\\"upstream_addr\\\":true,\\\"upstream_status\\\":true,\\\"upstream_connect_time\\\":false,\\\"upstream_header_time\\\":false,\\\"upstream_response_time\\\":true,\\\"all_upstream_response_time\\\":false,\\\"region_id\\\":false,\\\"auth_type\\\":false,\\\"http_x_forwarded_for\\\":true,\\\"http_user_agent\\\":true,\\\"error_type\\\":true,\\\"access_model2\\\":false,\\\"inner_time\\\":false,\\\"proxy_protocol_vni\\\":false,\\\"proxy_protocol_vpce_id\\\":false,\\\"proxy_protocol_addr\\\":false,\\\"body_bytes_sent\\\":false,\\\"api_name\\\":false,\\\"app_name\\\":false,\\\"provider_app_id\\\":false,\\\"provider_app_name\\\":false,\\\"custom_data_log01\\\":false,\\\"custom_data_log02\\\":false,\\\"custom_data_log03\\\":false,\\\"custom_data_log04\\\":false,\\\"custom_data_log05\\\":false,\\\"custom_data_log06\\\":false,\\\"custom_data_log07\\\":false,\\\"custom_data_log08\\\":false,\\\"custom_data_log09\\\":false,\\\"custom_data_log10\\\":false,\\\"response_source\\\":false},\\\"call_data\\\":{\\\"log_request_header\\\":false,\\\"request_header_filter\\\":\\\"\\\",\\\"log_request_query_string\\\":false,\\\"request_query_string_filter\\\":\\\"\\\",\\\"log_request_body\\\":false,\\\"log_response_header\\\":false,\\\"response_header_filter\\\":\\\"\\\",\\\"log_response_body\\\":false,\\\"custom_authorizer\\\":{\\\"frontend\\\":[],\\\"backend\\\":[]}}}}",
        "remark" : "Kafka log push",
        "create_time" : "2022-11-02T12:31:23.353Z",
        "update_time" : "2022-11-02T12:31:23.353Z"
      }

-  Example 5

   .. code-block::

      {
        "plugin_id" : "8b5253ed723c4a878e7b8532c08763b4",
        "plugin_name" : "Circuit Breaker Plug-in",
        "plugin_type" : "breaker",
        "plugin_scope" : "app",
        "plugin_content" : "{\\\"breaker_condition\\\":{\\\"breaker_type\\\":\\\"timeout\\\",\\\"breaker_mode\\\":\\\"counter\\\",\\\"unhealthy_condition\\\":\\\"\\\",\\\"unhealthy_threshold\\\":30,\\\"min_call_threshold\\\":20,\\\"unhealthy_percentage\\\":51,\\\"time_window\\\":15,\\\"open_breaker_time\\\":15},\\\"downgrade_default\\\":null,\\\"downgrade_parameters\\\":null,\\\"downgrade_rules\\\":null,\\\"scope\\\":\\\"basic\\\"}",
        "remark" : "Circuit breaker",
        "create_time" : "2022-11-02T12:31:23.353Z",
        "update_time" : "2022-11-02T12:31:23.353Z"
      }

-  Example 6

   .. code-block::

      {
        "plugin_id" : "235d97683439437585aff06020059720",
        "plugin_name" : "Third-Party Authentication Plug-in",
        "plugin_type" : "third_auth",
        "plugin_scope" : "global",
        "plugin_content" : "{\\\"auth_request\\\":{\\\"method\\\":\\\"POST\\\",\\\"protocol\\\":\\\"HTTP\\\",\\\"url_domain\\\":\\\"xxx.xxx.xxx.xxx:1234\\\",\\\"path\\\":\\\"/check\\\",\\\"timeout\\\":10,\\\"vpc_channel_enabled\\\":false,\\\"vpc_channel_info\\\":null},\\\"identities\\\":{\\\"headers\\\":[{\\\"name\\\":\\\"token\\\"}],\\\"queries\\\":null},\\\"carry_body\\\":{\\\"enabled\\\":true,\\\"max_body_size\\\":10000},\\\"carry_path_enabled\\\":false,\\\"return_resp_body_enabled\\\":true,\\\"carry_resp_headers\\\":[\\\"x-message-result\\\"],\\\"simple_auth_mode_enabled\\\":false,\\\"match_auth\\\":{\\\"key\\\":\\\"x-message-result\\\",\\\"value\\\":\\\"success\\\"},\\\"parameters\\\":[{\\\"type\\\":\\\"path\\\",\\\"name\\\":\\\"reqPath\\\",\\\"value\\\":\\\"reqPath\\\"},{\\\"type\\\":\\\"method\\\",\\\"name\\\":\\\"method\\\",\\\"value\\\":\\\"method\\\"},{\\\"type\\\":\\\"header\\\",\\\"name\\\":\\\"Host\\\",\\\"value\\\":\\\"Host\\\"}],\\\"rules\\\":[{\\\"rule_name\\\":\\\"allow2\\\",\\\"match_regex\\\":\\\"[\\\\\\\"OR\\\\\\\", [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/xxl-job-admin/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/leave/infor/v1/addLeaveLnfor\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/v1/charge/home/modifyChargeSync\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/mweb/campaign/api/v1/getActivityConfig\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/mp/vehicle/owner/home\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/mweb/campaign/api/v1/getTime\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/c-showroom-service/v1/vehicleDetails/upload\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/operation-charging-bff/carOwnerRights/certificate/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/api/2c/v1/sales-bff/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/2c/v1/vehicleDetails/upload\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"~~\\\\\\\", \\\\\\\"/operation-admin/*\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/app/settings/api/v1/receiveClk\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/vehicle/relative/yTSendVehicleControl.json\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/appoint/getAppointmentByTestDrive\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/callBackEvdPay\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/callBackEvdOrder\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/getUserToken\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/evd/callBackEvdCoupon\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/api/task/busTriggerTaskEvent.json\\\\\\\"], [\\\\\\\"reqPath\\\\\\\", \\\\\\\"==\\\\\\\", \\\\\\\"/datacenter-log-center/api/trackApi/commonAdd.json\\\\\\\"]]\\\"}],\\\"rule_type\\\":\\\"allow\\\",\\\"rule_enabled\\\":true,\\\"custom_forbid_limit\\\":100,\\\"auth_downgrade_enable\\\":false}",
        "remark" : "This is a third-party authentication plug-in that contains a rule expression blacklist.",
        "create_time" : "2023-05-06T06:54:59.296181801Z",
        "update_time" : "2023-05-06T07:07:18.369017889Z"
      }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error_code" : "APIG.3326",
     "error_msg" : "The plugin name already exists"
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "APIG.1002",
     "error_msg" : "Incorrect token or token resolution failed"
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "APIG.1005",
     "error_msg" : "No permissions to request this method"
   }

**Status code: 404**

Not Found

.. code-block::

   {
     "error_code" : "APIG.3068",
     "error_msg" : "Plugin b294018ee0554156a875b3513e02e5b9 does not exist"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIG.9999",
     "error_msg" : "System error"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
400         Bad Request
401         Unauthorized
403         Forbidden
404         Not Found
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
