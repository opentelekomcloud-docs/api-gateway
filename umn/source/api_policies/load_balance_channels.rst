:original_name: apig_03_0040.html

.. _apig_03_0040:

Load Balance Channels
=====================

Load balance channels expose your services through **dedicated gateways**, and are accessed through subnets in VPCs for lower latency. The server channel balances loads of backend services while the microservice channel automatically synchronizes service node changes.

After creating a load balance channel, you can configure it for an API of an HTTP&HTTPS backend service.

For example, six ECSs have been deployed, and a load balance channel has been created to reach ECS 01 and ECS 04. In this situation, APIG can access these two ECSs through the channel.


.. figure:: /_static/images/en-us_image_0000001278830029.png
   :alt: **Figure 1** Accessing ECSs in a load balance channel through APIG

   **Figure 1** Accessing ECSs in a load balance channel through APIG

Prerequisites
-------------

-  You have the **VPC Administrator** permission.
-  To configure a server channel, ensure that you have created cloud servers that can communicate with APIG.
-  To configure a Cloud Container Engine (CCE) microservice channel, ensure that you have created a cluster (a CCE cluster of VPC network model or a Turbo cluster) and a workload. For details, see section "Creating a CCE Standard/Turbo Cluster" or "Creating a Workload" in the *CCE User Guide*.

   .. important::

      -  If your gateway does not support microservice channels, contact technical support to upgrade the gateway to the latest version.
      -  The CCE cluster and the target gateway must be in the same VPC or connected to each other using a VPC peering connection. If the network is connected through the same VPC (with extended network segments) or a VPC peering connection, you need to add the container CIDR block of the cluster to **Routes** on the gateway details page.
      -  The workload must have a pod label configured. This label will be used to identify the workload, for example, a specific version of the workload, during :ref:`microservice configuration <apig_03_0040__en-us_topic_0000001221455657_table12731423111111>`. For details, see section "Labels and Annotations" in the *CCE User Guide*.

         -  Configure a pod label when you create a workload by clicking **Create Workload**. On the workload creation page, in the **Advanced Settings** > **Labels and Annotations** > **Pod Label** area, configure the **app** label.

         -  Configure a pod label when you create a workload by creating a YAML file. For example: **app=service01**.

            .. code-block::

               spec:
                 replicas: 2
                 selector:
                   matchLabels:
                     app: 'service01'

Creating a Load Balance Channel
-------------------------------

#. Go to the APIG console.
#. Select a gateway at the top of the navigation pane.
#. In the navigation pane, choose **API Management** > **API Policies**.

4. Click the **Load Balance Channels** tab.

5. Click **Create Load Balance Channel** and configure basic information.

   .. table:: **Table 1** Basic information

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================+
      | Name                              | Channel name.                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Port                              | The host port of the channel, that is, the port of your backend services.                                                                                                                         |
      |                                   |                                                                                                                                                                                                   |
      |                                   | Range: 1-65535                                                                                                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Routing Algorithm                 | The algorithm to be used to forward requests to cloud servers you select.                                                                                                                         |
      |                                   |                                                                                                                                                                                                   |
      |                                   | The following routing algorithms are available:                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                   |
      |                                   | -  **WRR**: weighted round robin                                                                                                                                                                  |
      |                                   | -  **WLC**: weighted least connection                                                                                                                                                             |
      |                                   | -  **SH**: source hashing                                                                                                                                                                         |
      |                                   | -  **URI hashing**                                                                                                                                                                                |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | -  **Server**: API requests will be distributed to ECSs or specified server IP addresses in the channel. For details, see :ref:`6 <apig_03_0040__en-us_topic_0000001221455657_li89941820153810>`. |
      |                                   | -  **Microservice**: API requests will be distributed to microservice IP addresses in the channel. For details, see :ref:`7 <apig_03_0040__en-us_topic_0000001221455657_li723312451176>`.         |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6. .. _apig_03_0040__en-us_topic_0000001221455657_li89941820153810:

   Configure servers if **Type** is set to **Server**.

   .. note::

      Load balance channels support private network load balancers. You can specify server addresses.

   -  Select cloud servers

      a. Click **Create Server Group**.

         In the displayed dialog box, enter server group information and click **OK**.

         .. _apig_03_0040__en-us_topic_0000001221455657_table189751910102116:

         .. table:: **Table 2** Server group parameters

            +-------------+------------------------------------------------------------------------------------------------------------------------------+
            | Parameter   | Description                                                                                                                  |
            +=============+==============================================================================================================================+
            | Group Name  | Enter a server group name. Using naming rules facilitates future search.                                                     |
            +-------------+------------------------------------------------------------------------------------------------------------------------------+
            | Weight      | Enter the weight of the server group. The larger the weight, the more requests can be forwarded to the servers in the group. |
            +-------------+------------------------------------------------------------------------------------------------------------------------------+
            | Description | Enter a brief description of the server group.                                                                               |
            +-------------+------------------------------------------------------------------------------------------------------------------------------+

      b. Click **Add Cloud Server**.

         In the displayed dialog box, select a subnet, select the cloud servers to be added, and click **OK**.

      c. After the configuration is complete, :ref:`configure health check <apig_03_0040__en-us_topic_0000001221455657_li5341536113812>`.

   -  Specify IP addresses

      a. Click **Create Server Group**.

         In the displayed dialog box, enter server group information and click **OK**. Configure parameters according to :ref:`Table 2 <apig_03_0040__en-us_topic_0000001221455657_table189751910102116>`.

      b. Click **Add Backend Server Address** and enter a backend server address.

         .. table:: **Table 3** Backend server parameters

            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
            | Parameter                         | Description                                                                                                                  |
            +===================================+==============================================================================================================================+
            | Backend Server Address            | Backend server IP address.                                                                                                   |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
            | Standby Node                      | If you enable this option, the backend server serves as a standby node. It works only when all non-standby nodes are faulty. |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
            | Port                              | Access port number of the backend server. If the port number is **0**, the port of the load balance channel is used.         |
            |                                   |                                                                                                                              |
            |                                   | The port number ranges from 0 to 65535.                                                                                      |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
            | Server Status                     | Specify whether to enable the server. Requests are distributed to the server only if it is enabled.                          |
            +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+

      c. After the configuration is complete, :ref:`configure health check <apig_03_0040__en-us_topic_0000001221455657_li5341536113812>`.

7. .. _apig_03_0040__en-us_topic_0000001221455657_li723312451176:

   Configure the microservice and server groups if **Type** is set to **Microservice**.

   |image1|

   a. Configure microservice information according to the following table.

      .. _apig_03_0040__en-us_topic_0000001221455657_table12731423111111:

      .. table:: **Table 4** CCE microservice configuration

         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                 |
         +===================================+=============================================================================================================================================================================================================================+
         | Microservice Type                 | Fixed as **Cloud Container Engine (CCE)**.                                                                                                                                                                                  |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Cluster                           | Select a cluster. Click **View CCE Console** to view the available clusters.                                                                                                                                                |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Namespace                         | Namespace of the cluster, which is an abstract collection of resources and objects.                                                                                                                                         |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Workload Type                     | -  **Deployment**: Deployments do not store any data or status while they are running.                                                                                                                                      |
         |                                   | -  **StatefulSet**: StatefulSets store data and statuses while they are running.                                                                                                                                            |
         |                                   | -  **DaemonSet**: DaemonSets ensure that only one pod runs on all or some nodes. When a node is added to a cluster, a new pod is also added for the node. When a node is removed from a cluster, the pod is also reclaimed. |
         |                                   |                                                                                                                                                                                                                             |
         |                                   |    .. note::                                                                                                                                                                                                                |
         |                                   |                                                                                                                                                                                                                             |
         |                                   |       If a DaemonSet is deleted, all pods created by it will be deleted.                                                                                                                                                    |
         |                                   |                                                                                                                                                                                                                             |
         |                                   | For details about workload types, see section "Workload Overview" in the *CCE User Guide*.                                                                                                                                  |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Service Label Key                 | Pod label of a workload. The service label name is the pod label key and the service label value is the pod label value.                                                                                                    |
         |                                   |                                                                                                                                                                                                                             |
         |                                   | For details about pod labels, see section "Labels and Annotations" in the *CCE User Guide*.                                                                                                                                 |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Service Label Value               |                                                                                                                                                                                                                             |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Configure a server group.

      Click **Add Server Group** and set required parameters.

      .. table:: **Table 5** Server group configuration of CCE microservice

         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                               |
         +===================================+===========================================================================================================================================================+
         | Server Group Name                 | Same as the service label value by default. Modify the name if necessary.                                                                                 |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Weight                            | Default value: **1**; range: 0-100.                                                                                                                       |
         |                                   |                                                                                                                                                           |
         |                                   | .. note::                                                                                                                                                 |
         |                                   |                                                                                                                                                           |
         |                                   |    If **Routing Algorithm** is set to **URI hashing**, the weight is **1** by default and cannot be changed.                                              |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Backend Service Port              | The port used by the backend server. If no port number is specified or the port number is **0**, the port of the load balance channel is used by default. |
         |                                   |                                                                                                                                                           |
         |                                   | The port number ranges from 0 to 65535.                                                                                                                   |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Workload Name                     | Select a CCE workload.                                                                                                                                    |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Tag                               | Pod label of a workload. If a workload cannot be identified by certain service label name and value, select another pod label to specify the workload.    |
         |                                   |                                                                                                                                                           |
         |                                   | For example, workloads **01** and **02** have the same **app** label, but they can be identified using the **version** or **test_name** tag.              |
         |                                   |                                                                                                                                                           |
         |                                   | Workload **01**                                                                                                                                           |
         |                                   |                                                                                                                                                           |
         |                                   | .. code-block::                                                                                                                                           |
         |                                   |                                                                                                                                                           |
         |                                   |    spec:                                                                                                                                                  |
         |                                   |      replicas: 2                                                                                                                                          |
         |                                   |      selector:                                                                                                                                            |
         |                                   |        matchLabels:                                                                                                                                       |
         |                                   |          app: 'app01'                                                                                                                                     |
         |                                   |          version: 'v1'                                                                                                                                    |
         |                                   |                                                                                                                                                           |
         |                                   | Workload **02**                                                                                                                                           |
         |                                   |                                                                                                                                                           |
         |                                   | .. code-block::                                                                                                                                           |
         |                                   |                                                                                                                                                           |
         |                                   |    spec:                                                                                                                                                  |
         |                                   |      replicas: 2                                                                                                                                          |
         |                                   |      selector:                                                                                                                                            |
         |                                   |        matchLabels:                                                                                                                                       |
         |                                   |          app: 'app01'                                                                                                                                     |
         |                                   |          test_name: 'test_value'                                                                                                                          |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. After the configuration is complete, :ref:`configure health check <apig_03_0040__en-us_topic_0000001221455657_li5341536113812>`.

8. .. _apig_03_0040__en-us_topic_0000001221455657_li5341536113812:

   Configure health checks.

   .. table:: **Table 6** Basic information

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                      |
      +===================================+==================================================================================================================================================================================================================================================+
      | Protocol                          | The protocol used to perform health checks on cloud servers associated with the channel. Options:                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | -  TCP                                                                                                                                                                                                                                           |
      |                                   | -  HTTP                                                                                                                                                                                                                                          |
      |                                   | -  HTTPS                                                                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Default value: **TCP**.                                                                                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Two-Way Authentication            | **Set this parameter only when Protocol is set to HTTPS.**                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Determine whether to allow APIG to authenticate the API backend service. For details about how to configure the certificate for two-way authentication, see :ref:`Procedure <apig_03_0039__en-us_topic_0000001222396877_section31331424142717>`. |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Path                              | **Set this parameter only when Protocol is not set to TCP.**                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | The destination path for health checks.                                                                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Method                            | -  GET                                                                                                                                                                                                                                           |
      |                                   | -  HEAD                                                                                                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Check Port                        | The destination port for health checks.                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | If this parameter is not specified, the port of the load balance channel is used by default.                                                                                                                                                     |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Healthy Threshold                 | The number of consecutive successful checks required for a cloud server to be considered healthy.                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Range: 2-10. Default value: **2**                                                                                                                                                                                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Unhealthy Threshold               | The number of consecutive failed checks required for a cloud server to be considered unhealthy.                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Range: 2-10. Default value: **5**.                                                                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Timeout (s)                       | The timeout used to determine whether a health check has failed. Unit: s.                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Range: 2-30. Default value: **5**.                                                                                                                                                                                                               |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Interval (s)                      | The interval between consecutive checks. Unit: s.                                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | Range: 5-300. Default value: **10**.                                                                                                                                                                                                             |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Response Codes                    | **Set this parameter only when Protocol is not set to TCP.**                                                                                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                                  |
      |                                   | The HTTP codes used to check for a successful response from a target.                                                                                                                                                                            |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

9. Click **Finish**.

   For a microservice channel, adding, deleting, or modifying a pod IP address of the CCE workload will also change the backend server address of the channel.

Follow-Up Operations
--------------------

#. Ensure that a route has been added to the gateway. **To connect a CCE workload to a gateway through the same VPC (with extended network segments) or a VPC peering connection, you need to add a route.**

   a. Log in to the CCE console, choose **Clusters**, and click the name of the created CCE cluster.
   b. In the **Networking Configuration** area on the **Cluster Details** page, view and record the container CIDR block.
   c. Log in to the APIG console and click the gateway name on the **Gateways** page.
   d. In the **Routes** area on the **Gateway Information** page, check whether the added route is consistent with the container CIDR block. If not, add the correct route.

#. :ref:`Create APIs <apig_03_0010>` to expose backend services deployed in the workload.

.. |image1| image:: /_static/images/en-us_image_0000001418236376.png
