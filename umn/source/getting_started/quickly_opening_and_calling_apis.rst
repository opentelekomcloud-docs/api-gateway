:original_name: apig-ug-180307002.html

.. _apig-ug-180307002:

Quickly Opening and Calling APIs
================================

This section describes how to quickly get started with APIG. The following uses **simple authentication** with an app as an example to describe how to quickly open and call APIs. **Simple authentication supports API calling only in HTTPS or gRPCS mode.**


.. figure:: /_static/images/en-us_image_0000001944266238.png
   :alt: **Figure 1** Using APIG

   **Figure 1** Using APIG

#. :ref:`Preparations <apig-ug-180307002__en-us_topic_0000001960420837_section91241035113112>`

   Before using APIG, ensure you have configured a VPC, subnet, and security group.

#. :ref:`Create a gateway <apig-ug-180307002__en-us_topic_0000001960420837_section1256595695319>`

   Create a gateway with appropriate specifications.

#. :ref:`Open the API <apig-ug-180307002__en-us_topic_0000001960420837_section445913185541>`

   Create an API that supports simple authentication with Mock backend. Debug the created API and publish it.

#. :ref:`Call the API <apig-ug-180307002__en-us_topic_0000001960420837_section46581949195412>`

   Create a credential and add an AppCode. Then use an API test tool to call the API with the AppCode.

Constraints
-----------

Security groups do not take effect after gateways are created in regions. To disable access from specific IP addresses, see :ref:`Configuring API Access Control <apig_03_0027>`.

.. _apig-ug-180307002__en-us_topic_0000001960420837_section91241035113112:

Step 1: Preparations
--------------------

#. Before creating an APIG gateway, ensure that your account has permissions to perform operations on APIG gateways.

   -  You must be assigned both the **APIG Administrator** and **VPC Administrator** roles so that you can create gateways.
   -  Alternatively, you must be attached the **APIG FullAccess** policy.
   -  To achieve fine-grained management of your cloud resources, create IAM user groups and users and grant specified permissions to the users. For details, see :ref:`Creating a User and Granting APIG Permissions <apig_03_0050>`.

#. Before creating an APIG gateway, ensure that a VPC and a subnet are available.

   Configure a VPC and subnet for the APIG gateway as required. You can use the current account's existing VPC and subnet or create new ones. For details about how to create a VPC and subnet, see section "Creating a VPC and Subnet" in the *Virtual Private Cloud User Guide*. **Note that the created VPC and APIG gateway must be in the same region.**

#. Before creating an APIG gateway, ensure that a security group is available.

   Configure the security group for APIG gateways as required. You can use the current account's existing security groups, or create new ones. For details, see "Creating a Security Group" in *Virtual Private Cloud User Guide*.

   To connect to APIG gateways, add the security group rules described in :ref:`Table 1 <apig-ug-180307002__en-us_topic_0000001960420837_table161395381402>`. Other rules can be added based on site requirements.

   .. _apig-ug-180307002__en-us_topic_0000001960420837_table161395381402:

   .. table:: **Table 1** Security group rule

      ========= ======== ====== ============== ================
      Direction Protocol Port   Source address Description
      ========= ======== ====== ============== ================
      Inbound   TCP      80/443 0.0.0.0/0      Intra-VPC Access
      ========= ======== ====== ============== ================

   .. note::

      -  After a security group is created, it has a default inbound rule that allows communication among ECSs within the security group and a default outbound rule that allows all outbound traffic. If you access your APIG gateway using the private network within a VPC, you do not need to add the rules described in :ref:`Table 1 <apig-ug-180307002__en-us_topic_0000001960420837_table161395381402>`.
      -  Security groups do not take effect after gateways are created in regions. To disable access from specific IP addresses, see :ref:`Configuring API Access Control <apig_03_0027>`.

.. _apig-ug-180307002__en-us_topic_0000001960420837_section1256595695319:

Step 2: Create a gateway
------------------------

#. Go to the APIG console.
#. Configure the gateway according to the following table.

   .. table:: **Table 2** Configuring the gateway

      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Description                                                                                                                                      |
      +=======================+==================================================================================================================================================+
      | Region                | The region to which the gateway belongs.                                                                                                         |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                    | The AZ of the gateway. Select **AZ1**, **AZ2**, and **AZ3**.                                                                                     |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Gateway Name          | Enter the gateway name, for example, **apig-test**.                                                                                              |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Edition               | Gateway specifications. Select **Basic**.                                                                                                        |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Scheduled Maintenance | The period for gateway maintenance. Retain the default value.                                                                                    |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project    | Select **default**.                                                                                                                              |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Public Inbound Access | Determine whether to allow the APIs created in the gateway to be called by external services using an EIP. Enable the **Public Inbound Access**. |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | VPC                   | Select the prepared VPC and subnet.                                                                                                              |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group        | Select the prepared security group.                                                                                                              |
      +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Next**.
#. Confirm the configuration and click **Pay Now**.

.. _apig-ug-180307002__en-us_topic_0000001960420837_section445913185541:

Step 3: Open the API
--------------------

#. Create an API.

   a. In the navigation pane, choose **API Management** > **APIs**.
   b. Click **Create API** > **Create API** and configure the frontend.

      .. table:: **Table 3** Frontend definition

         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                   |
         +===================================+===============================================================================================================================================================================+
         | API Name                          | Enter the API name, for example, **API_test**.                                                                                                                                |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Group                             | Select the default group **DEFAULT**. To create a group, click **Create API Group**. For details about how to create an API, see :ref:`Creating an API Group <apig_03_0005>`. |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | URL                               | **Method**: Request method of the API. Set this parameter to **GET**.                                                                                                         |
         |                                   |                                                                                                                                                                               |
         |                                   | **Protocol**: Set this parameter to **HTTPS**.                                                                                                                                |
         |                                   |                                                                                                                                                                               |
         |                                   | **Subdomain Name**: The subdomain automatically allocated to the API group. The subdomain name of the **default** API group is used.                                          |
         |                                   |                                                                                                                                                                               |
         |                                   | Path: path of the API request. Set this parameter to **/test**.                                                                                                               |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Gateway Response                  | The response to be displayed if APIG fails to process an API request. Default: **default**.                                                                                   |
         +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   c. Configure security settings based on the following table.

      .. table:: **Table 4** API request definition

         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter             | Description                                                                                                                                                                  |
         +=======================+==============================================================================================================================================================================+
         | Authentication Mode   | API authentication mode. Set this parameter to **App**.                                                                                                                      |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Simple Authentication | If you enable this option, API Gateway verifies only the AppCode and the request signature does not need to be verified. For this example, enable **Simple Authentication**. |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   d. Click **Next** and configure the default backend information.

      .. table:: **Table 5** Parameters for defining a Mock backend service

         +--------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter    | Description                                                                                                                                                                                                                                                                                                                        |
         +==============+====================================================================================================================================================================================================================================================================================================================================+
         | Backend Type | Backend service type. Select **Mock** to prevent API requests from being forwarded to the backend service. This is useful if you need to debug APIs when the backend is unavailable. If a backend service is available, configure other backend service types as required. For details, see :ref:`Creating an API <apig_03_0128>`. |
         +--------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Status Code  | The HTTP status code returned by the API. Use the default **200** here.                                                                                                                                                                                                                                                            |
         +--------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Response     | Expected result to the API caller for debugging and verification. Enter **success** here.                                                                                                                                                                                                                                          |
         +--------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   e. Click **Finish**.

#. Debug the API.

   a. On the **APIs** tab page, select an API and click **Debug**.

   b. Click **Debug** on the right of the URL. The API request and response information are displayed at the bottom of the page.

      If the API is successfully called, the status code **200** is displayed, and **success** is returned for the Mock backend. Otherwise, rectify the fault by referring to :ref:`Error Codes <apig_03_0048>`.

#. Publish the API.

   a. On the **APIs** tab, click **Publish Latest Version**.
   b. Select the environment in which the API is to be published. Choose the default environment **RELEASE**. Or you can click **Create Environment** to create an environment. For details, see :ref:`(Optional) Configuring the Environment and Environment Variables <apig_03_0007>`.
   c. Click **OK**.

.. _apig-ug-180307002__en-us_topic_0000001960420837_section46581949195412:

Step 4: Call the API
--------------------

#. Create a credential.

   a. In the navigation pane, choose **API Management** > **Credentials**.
   b. Click **Create Credential** and enter the credential name. In this example, enter **apptest**.
   c. Click **OK**.

#. Bind the credential to the API. **Note that only APIs that use app authentication can be bound.**

   a. In the **Operation** column of the created credential, click **Select APIs**.
   b. Select an environment, API group, and APIs.
   c. Click **OK**.

#. Add an AppCode.

   a. In the credential list, click the created credential to go to the credential details page.
   b. Under **AppCodes**, click **Add AppCode**.
   c. Select **Automatically generated**.
   d. Click **OK**.

#. Call the API.

   Use the API test tool to configure the API request and authentication.

   a. Select **GET** as the request method. On the **APIs** page, copy the URL in the format of **https://debugging domain name/path** to the API test tool.

   b. Add the header parameter **X-Apig-AppCode** and set the parameter value to the generated AppCode.

   c. Send the request.

      If the API is successfully called, the status code **200** is displayed, and **success** is returned for the Mock backend. Otherwise, rectify the fault by referring to :ref:`Error Codes <apig_03_0048>`.

      |image1|

Related Documents
-----------------

-  For details about how to create an API, see :ref:`Creating an API <apig_03_0128>`.
-  For more information about API calling, see :ref:`Calling an API <apig_03_0046__section19907427165210>`.
-  If an API fails to be called, refer to :ref:`Error Codes <apig_03_0048>`.
-  VPC owners can share the subnet in the VPC with one or multiple accounts through Resource Access Manager (RAM). Through VPC sharing, you can easily configure, operate, and manage multiple accounts' resources at low costs. For more information about VPC subnet sharing, see section "VPC Sharing Overview" in the *Virtual Private Cloud User Guide*.

.. |image1| image:: /_static/images/en-us_image_0000001975861969.png
