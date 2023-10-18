:original_name: en-us_topic_0000001174497029.html

.. _en-us_topic_0000001174497029:

Log Analysis
============

Scenario
--------

This section describes how to obtain and analyze the API calling logs of dedicated gateways.

Prerequisites
-------------

APIs have been called.

Procedure
---------

#. Log in to the management console.

#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.

#. Choose **API Calling > Access Logs**, and click **Configure Log Collection**.

#. Enable log collection (|image1|).

#. Specify a log group and log stream, and click **OK**. For details about log groups and log streams, see *Log Tank Service User Guide*.

#. Click **Log Fields** to view the description of each log field. Then view and analyze logs by referring to the log field descriptions.

#. To export logs, see section "Log Transfer" in the *Log Tank Service User Guide*.

   Fields in access logs are separated using spaces. The following table describes each log field.

   .. table:: **Table 1** Log field description

      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | No. | Field                  | Description                                                                                                   |
      +=====+========================+===============================================================================================================+
      | 1   | remote_addr            | Client IP address                                                                                             |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 2   | request_id             | Request ID                                                                                                    |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 3   | api_id                 | API ID                                                                                                        |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 4   | user_id                | Project ID provided by a requester for IAM authentication                                                     |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 5   | app_id                 | App ID provided by a requester for app-based authentication                                                   |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 6   | time_local             | Time when a request is received                                                                               |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 7   | request_time           | Request latency                                                                                               |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 8   | request_method         | HTTP request method                                                                                           |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 9   | host                   | Domain name                                                                                                   |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 10  | router_uri             | Request URI                                                                                                   |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 11  | server_protocol        | Request protocol                                                                                              |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 12  | status                 | Response status code                                                                                          |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 13  | bytes_sent             | Response size in bytes, including the status line, header, and body.                                          |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 14  | request_length         | Request length in bytes, including the start line, header, and body.                                          |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 15  | http_user_agent        | User agent ID                                                                                                 |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 16  | http_x_forwarded_for   | X-Forwarded-For header field                                                                                  |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 17  | upstream_addr          | Backend address                                                                                               |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 18  | upstream_uri           | Backend URI                                                                                                   |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 19  | upstream_status        | Backend response code                                                                                         |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 20  | upstream_connect_time  | Time taken for establishing a connection with the backend                                                     |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 21  | upstream_header_time   | Duration from the beginning of the establishment of a connection to receiving the first byte from the backend |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 22  | upstream_response_time | Duration from the beginning of the establishment of a connection to receiving the last byte from the backend  |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+
      | 23  | region_id              | Region ID                                                                                                     |
      +-----+------------------------+---------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000001142927584.png
