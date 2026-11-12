:original_name: apig_03_0032.html

.. _apig_03_0032:

Monitoring Metrics
==================

This section describes the namespace, metrics, and dimension that APIG reports to the Cloud Eye service. You can view metrics and alarms by using the Cloud Eye console.

.. note::

   -  Cloud Eye supports a maximum of four hierarchical dimensions that are numbered from 0 to 3. For example, if the dimension of a metric is **instance_id,api_id**, **instance_id** indicates level 0 and **api_id** indicates level 1.
   -  If a metric is not supported by your gateway, contact technical support to upgrade the gateway to the latest version.

Namespace
---------

SYS.APIC

Metrics
-------

.. table:: **Table 1** Metric description

   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | Metric ID         | Metric Name         | Description                                                                                                                                            | Value Range | Unit      | Conversion Rule | Dimension                           | Monitoring Period (Minute) |
   +===================+=====================+========================================================================================================================================================+=============+===========+=================+=====================================+============================+
   | throttled_calls   | Throttled API Calls | Number of API calls that are throttled.                                                                                                                | >= 0        | Times/min | None            | Dedicated gateway (instance_id)     | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | requests          | API Calls           | Number of times that an API has been called                                                                                                            | >= 0        | Times/min | None            | Dedicated gateway (instance_id)     | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | req_count_error   | Total Errors        | Total number of API errors                                                                                                                             | >= 0        | Times/min | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | req_count_5xx     | 5xx Responses       | Number of API calls resulting in 5xx responses                                                                                                         | >= 0        | Times/min | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | req_count_4xx     | 4xx Responses       | Number of API calls resulting in 4xx responses                                                                                                         | >= 0        | Times/min | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | req_count_2xx     | 2xx Responses       | Number of API calls resulting in 2xx responses                                                                                                         | >= 0        | Times/min | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | req_count         | API Calls           | Number of times that an API has been called                                                                                                            | >= 0        | Times/min | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | output_throughput | Outgoing Traffic    | Outgoing traffic of the API                                                                                                                            | >= 0        | Byte      | 1000(SI)        | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | max_latency       | Maximum Latency     | Maximum latency of the API                                                                                                                             | >= 0        | ms        | None            | Dedicated gateway (instance_id)     | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | max_latency       | Maximum Latency     | Maximum latency of the API                                                                                                                             | >= 0        | ms        | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | input_throughput  | Incoming Traffic    | Incoming traffic of the API                                                                                                                            | >= 0        | Byte      | 1000(SI)        | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | error_5xx         | 5xx Responses       | Number of API calls resulting in 5xx responses                                                                                                         | >= 0        | Times/min | None            | Dedicated gateway (instance_id)     | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | error_4xx         | 4xx Responses       | Number of API calls resulting in 4xx responses                                                                                                         | >= 0        | Times/min | None            | Dedicated gateway (instance_id)     | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | avg_latency       | Average Latency     | Average latency of the API                                                                                                                             | >= 0        | ms        | None            | Dedicated gateway (instance_id)     | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | avg_latency       | Average Latency     | Average latency of the API                                                                                                                             | >= 0        | ms        | None            | API (instance_id,api_id)            | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | node_system_load  | Node System Load    | Load details of a gateway node on the data plane. **1** means a low water level, **2** means a medium water level, and **3** means a high water level. | **1, 2, 3** | count     | None            | Gateway node (instance_id, node_ip) | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | node_cpu_usage    | Node CPU Usage      | CPU usage details of a gateway node on the data plane                                                                                                  | >= 0        | %         | None            | Gateway node (instance_id, node_ip) | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+
   | node_memory_usage | Node Memory Usage   | Memory usage details of a gateway node on the data plane                                                                                               | >= 0        | %         | None            | Gateway node (instance_id, node_ip) | 1                          |
   +-------------------+---------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+-------------+-----------+-----------------+-------------------------------------+----------------------------+

If a monitored object has multiple dimensions, the dimensional level of specific metrics is required when you use APIs to query the metrics.

For example, if you want to query the number of times a single API is called, the dimension of the metric is **instance_id,api_id**, indicating that **instance_id** is level 0 and **api_id** is level 1.

-  For example, to query a single metric by calling the API, set the **api_id** dimension as follows:

   .. code-block::

      dim.0=instance_id,3d65c1ac9a9f4c5fa05435184a087bb2&dim.1=api_id,6666cd76f96956469e7be39d750cc7d9

   **3d65c1ac-9a9f-4c5f-a054-35184a087bb2** and **6666cd76f96956469e7be39d750cc7d9** are the values of **instance_id** and **api_id**, respectively. For details about how to obtain the values, see :ref:`Dimension <apig_03_0032__en-us_topic_0106543506_section03914451951>`.

-  For example, to batch query metrics by calling the API, set the **api_id** dimension as follows:

   .. code-block::

      "dimensions": [
                       {
                           "name": "instance_id",
                           "value": "3d65c1ac9a9f4c5fa05435184a087bb2"
                       },
                       {
                           "name": "api_id",
                           "value": "6666cd76f96956469e7be39d750cc7d9"
                       }
                   ]

   **3d65c1ac9a9f4c5fa05435184a087bb2** and **6666cd76f96956469e7be39d750cc7d9** are the values of **instance_id** and **api_id**, respectively. For details about how to obtain the values, see :ref:`Dimension <apig_03_0032__en-us_topic_0106543506_section03914451951>`.

.. _apig_03_0032__en-us_topic_0106543506_section03914451951:

Dimension
---------

.. table:: **Table 2** Dimension definition

   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | Key                               | Value                                                                                                                 |
   +===================================+=======================================================================================================================+
   | instance_id                       | ID of a dedicated gateway, for example, **8df0xxxx000p**.                                                             |
   |                                   |                                                                                                                       |
   |                                   | To obtain the value, call the API for querying dedicated gateways and extract it from the response parameters.        |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id, node_ip              | A node of a dedicated gateway, for example, **8df0xxxx000p,192.168.10.10**.                                           |
   |                                   |                                                                                                                       |
   |                                   | To obtain the value, call the API for querying dedicated gateway details and extract it from the response parameters. |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+
   | instance_id, api_id               | An API, for example, **8df0xxxx000p,6666xxxxc7d9**.                                                                   |
   |                                   |                                                                                                                       |
   |                                   | To obtain the value, call the API for querying APIs and extract it from the response parameters.                      |
   +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------+

Helpful Links
-------------

-  If a metric is abnormal, you can configure alarm rules to receive notifications in a timely manner. For details, see :ref:`Configuring an Alarm Rule <apig_03_0033>`.

-  For details about how to view APIG metrics, see :ref:`Viewing Metrics <apig_03_0034>`.
-  For details about how to view API calls, see :ref:`Viewing API Call Logs <apig_03_0042>`.
