:original_name: ListInstancesV2.html

.. _ListInstancesV2:

Querying Dedicated Gateways
===========================

Function
--------

This API is used to query dedicated gateways.

Calling Method
--------------

For details, see :ref:`Calling APIs <apig-api-180713003>`.

URI
---

GET /v2/{project_id}/apigw/instances

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                             |
   +============+===========+========+=========================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain it, see :ref:`Obtaining a Project ID <apig-api-180713009>`. |
   +------------+-----------+--------+---------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================================+
   | offset          | No              | Long            | Offset from which the query starts. If the value is less than 0, it is automatically converted to 0.                                                                                |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Default: **0**                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of items displayed on each page. A value less than or equal to 0 will be automatically converted to 20, and a value greater than 500 will be automatically converted to 500. |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Minimum: **1**                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Maximum: **500**                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Default: **20**                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id     | No              | String          | Gateway ID.                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_name   | No              | String          | Gateway name.                                                                                                                                                                       |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Gateway status.                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  Creating                                                                                                                                                                         |
   |                 |                 |                 | -  CreateSuccess                                                                                                                                                                    |
   |                 |                 |                 | -  CreateFail                                                                                                                                                                       |
   |                 |                 |                 | -  Initing                                                                                                                                                                          |
   |                 |                 |                 | -  Registering                                                                                                                                                                      |
   |                 |                 |                 | -  Running                                                                                                                                                                          |
   |                 |                 |                 | -  InitingFailed                                                                                                                                                                    |
   |                 |                 |                 | -  RegisterFailed                                                                                                                                                                   |
   |                 |                 |                 | -  Installing                                                                                                                                                                       |
   |                 |                 |                 | -  InstallFailed                                                                                                                                                                    |
   |                 |                 |                 | -  Updating                                                                                                                                                                         |
   |                 |                 |                 | -  UpdateFailed                                                                                                                                                                     |
   |                 |                 |                 | -  Rollbacking                                                                                                                                                                      |
   |                 |                 |                 | -  RollbackSuccess                                                                                                                                                                  |
   |                 |                 |                 | -  RollbackFailed                                                                                                                                                                   |
   |                 |                 |                 | -  Deleting                                                                                                                                                                         |
   |                 |                 |                 | -  DeleteFailed                                                                                                                                                                     |
   |                 |                 |                 | -  Unregistering                                                                                                                                                                    |
   |                 |                 |                 | -  UnRegisterFailed                                                                                                                                                                 |
   |                 |                 |                 | -  CreateTimeout                                                                                                                                                                    |
   |                 |                 |                 | -  InitTimeout                                                                                                                                                                      |
   |                 |                 |                 | -  RegisterTimeout                                                                                                                                                                  |
   |                 |                 |                 | -  InstallTimeout                                                                                                                                                                   |
   |                 |                 |                 | -  UpdateTimeout                                                                                                                                                                    |
   |                 |                 |                 | -  RollbackTimeout                                                                                                                                                                  |
   |                 |                 |                 | -  DeleteTimeout                                                                                                                                                                    |
   |                 |                 |                 | -  UnregisterTimeout                                                                                                                                                                |
   |                 |                 |                 | -  Starting                                                                                                                                                                         |
   |                 |                 |                 | -  Freezing                                                                                                                                                                         |
   |                 |                 |                 | -  Frozen                                                                                                                                                                           |
   |                 |                 |                 | -  Restarting                                                                                                                                                                       |
   |                 |                 |                 | -  RestartFail                                                                                                                                                                      |
   |                 |                 |                 | -  Unhealthy                                                                                                                                                                        |
   |                 |                 |                 | -  RestartTimeout                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                     |
   |                 |                 |                 | -  **Creating**                                                                                                                                                                     |
   |                 |                 |                 | -  **CreateSuccess**                                                                                                                                                                |
   |                 |                 |                 | -  **CreateFail**                                                                                                                                                                   |
   |                 |                 |                 | -  **Initing**                                                                                                                                                                      |
   |                 |                 |                 | -  **Registering**                                                                                                                                                                  |
   |                 |                 |                 | -  **Running**                                                                                                                                                                      |
   |                 |                 |                 | -  **InitingFailed**                                                                                                                                                                |
   |                 |                 |                 | -  **RegisterFailed**                                                                                                                                                               |
   |                 |                 |                 | -  **Installing**                                                                                                                                                                   |
   |                 |                 |                 | -  **InstallFailed**                                                                                                                                                                |
   |                 |                 |                 | -  **Updating**                                                                                                                                                                     |
   |                 |                 |                 | -  **UpdateFailed**                                                                                                                                                                 |
   |                 |                 |                 | -  **Rollbacking**                                                                                                                                                                  |
   |                 |                 |                 | -  **RollbackSuccess**                                                                                                                                                              |
   |                 |                 |                 | -  **RollbackFailed**                                                                                                                                                               |
   |                 |                 |                 | -  **Deleting**                                                                                                                                                                     |
   |                 |                 |                 | -  **DeleteFailed**                                                                                                                                                                 |
   |                 |                 |                 | -  **Unregistering**                                                                                                                                                                |
   |                 |                 |                 | -  **UnRegisterFailed**                                                                                                                                                             |
   |                 |                 |                 | -  **CreateTimeout**                                                                                                                                                                |
   |                 |                 |                 | -  **InitTimeout**                                                                                                                                                                  |
   |                 |                 |                 | -  **RegisterTimeout**                                                                                                                                                              |
   |                 |                 |                 | -  **InstallTimeout**                                                                                                                                                               |
   |                 |                 |                 | -  **UpdateTimeout**                                                                                                                                                                |
   |                 |                 |                 | -  **RollbackTimeout**                                                                                                                                                              |
   |                 |                 |                 | -  **DeleteTimeout**                                                                                                                                                                |
   |                 |                 |                 | -  **UnregisterTimeout**                                                                                                                                                            |
   |                 |                 |                 | -  **Starting**                                                                                                                                                                     |
   |                 |                 |                 | -  **Freezing**                                                                                                                                                                     |
   |                 |                 |                 | -  **Frozen**                                                                                                                                                                       |
   |                 |                 |                 | -  **Restarting**                                                                                                                                                                   |
   |                 |                 |                 | -  **RestartFail**                                                                                                                                                                  |
   |                 |                 |                 | -  **Unhealthy**                                                                                                                                                                    |
   |                 |                 |                 | -  **RestartTimeout**                                                                                                                                                               |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                        |
   +==============+===========+========+====================================================================================================================================================+
   | X-Auth-Token | Yes       | String | User token. It can be obtained by calling the IAM API used to obtain a user token. The value of X-Subject-Token in the response header is a token. |
   +--------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------+---------------------------------------------------------------------------------------+------------------------------------------------------+
   | Parameter | Type                                                                                  | Description                                          |
   +===========+=======================================================================================+======================================================+
   | size      | Integer                                                                               | Length of the returned resource list.                |
   +-----------+---------------------------------------------------------------------------------------+------------------------------------------------------+
   | total     | Long                                                                                  | Number of resources that match the query conditions. |
   +-----------+---------------------------------------------------------------------------------------+------------------------------------------------------+
   | instances | Array of :ref:`RespInstanceBase <listinstancesv2__response_respinstancebase>` objects | Gateway list.                                        |
   +-----------+---------------------------------------------------------------------------------------+------------------------------------------------------+

.. _listinstancesv2__response_respinstancebase:

.. table:: **Table 5** RespInstanceBase

   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                  | Description                                                                  |
   +=======================+=======================================================================================+==============================================================================+
   | id                    | String                                                                                | Gateway ID.                                                                  |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | project_id            | String                                                                                | ID of the tenant to which the gateway belongs.                               |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | instance_name         | String                                                                                | Gateway name.                                                                |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | status                | String                                                                                | Instance status:                                                             |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  Creating: The instance is being created.                                  |
   |                       |                                                                                       | -  CreateSuccess: The instance is created successfully.                      |
   |                       |                                                                                       | -  CreateFail: The instance fails to be created.                             |
   |                       |                                                                                       | -  Initing: The instance is being initialized.                               |
   |                       |                                                                                       | -  Registering: The instance is being registered.                            |
   |                       |                                                                                       | -  Running: The instance is running.                                         |
   |                       |                                                                                       | -  InitingFailed: The instance fails to be initialized.                      |
   |                       |                                                                                       | -  RegisterFailed: The instance fails to be registered.                      |
   |                       |                                                                                       | -  Installing: The instance is being installed.                              |
   |                       |                                                                                       | -  InstallFailed: The instance fails to be installed.                        |
   |                       |                                                                                       | -  Updating: The instance is being upgraded.                                 |
   |                       |                                                                                       | -  UpdateFailed: The instance fails to be upgraded.                          |
   |                       |                                                                                       | -  Rollbacking: The instance is being rolled back.                           |
   |                       |                                                                                       | -  RollbackSuccess: The instance is rolled back successfully.                |
   |                       |                                                                                       | -  RollbackFailed: The instance fails to be rolled back.                     |
   |                       |                                                                                       | -  Deleting: The instance is being deleted.                                  |
   |                       |                                                                                       | -  DeleteFailed: The instance fails to be deleted.                           |
   |                       |                                                                                       | -  Unregistering: The instance is being deregistered.                        |
   |                       |                                                                                       | -  UnRegisterFailed: The instance fails to be deregistered.                  |
   |                       |                                                                                       | -  CreateTimeout: Creation of the instance times out.                        |
   |                       |                                                                                       | -  InitTimeout: Initialization of the instance times out.                    |
   |                       |                                                                                       | -  RegisterTimeout: Registration of the instance times out.                  |
   |                       |                                                                                       | -  InstallTimeout: Installation of the instance times out.                   |
   |                       |                                                                                       | -  UpdateTimeout: Upgrading of the instance times out.                       |
   |                       |                                                                                       | -  RollbackTimeout: Rollback of the instance times out.                      |
   |                       |                                                                                       | -  DeleteTimeout: Deletion of the instance times out.                        |
   |                       |                                                                                       | -  UnregisterTimeout: Deregistration of the instance times out.              |
   |                       |                                                                                       | -  Starting: The instance is being started.                                  |
   |                       |                                                                                       | -  Freezing: The instance is being frozen.                                   |
   |                       |                                                                                       | -  Frozen: The instance is frozen.                                           |
   |                       |                                                                                       | -  Restarting: The instance is being restarted.                              |
   |                       |                                                                                       | -  RestartFail: The instance fails to be restarted.                          |
   |                       |                                                                                       | -  Unhealthy: The instance is abnormal.                                      |
   |                       |                                                                                       | -  RestartTimeout: Restart of the instance times out.                        |
   |                       |                                                                                       | -  Resizing: The instance specification is changing.                         |
   |                       |                                                                                       | -  ResizeFailed: The instance specification fails to be changed.             |
   |                       |                                                                                       | -  ResizeTimeout: The instance specification change times out.               |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | Enumeration values:                                                          |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  **Creating**                                                              |
   |                       |                                                                                       | -  **CreateSuccess**                                                         |
   |                       |                                                                                       | -  **CreateFail**                                                            |
   |                       |                                                                                       | -  **Initing**                                                               |
   |                       |                                                                                       | -  **Registering**                                                           |
   |                       |                                                                                       | -  **Running**                                                               |
   |                       |                                                                                       | -  **InitingFailed**                                                         |
   |                       |                                                                                       | -  **RegisterFailed**                                                        |
   |                       |                                                                                       | -  **Installing**                                                            |
   |                       |                                                                                       | -  **InstallFailed**                                                         |
   |                       |                                                                                       | -  **Updating**                                                              |
   |                       |                                                                                       | -  **UpdateFailed**                                                          |
   |                       |                                                                                       | -  **Rollbacking**                                                           |
   |                       |                                                                                       | -  **RollbackSuccess**                                                       |
   |                       |                                                                                       | -  **RollbackFailed**                                                        |
   |                       |                                                                                       | -  **Deleting**                                                              |
   |                       |                                                                                       | -  **DeleteFailed**                                                          |
   |                       |                                                                                       | -  **Unregistering**                                                         |
   |                       |                                                                                       | -  **UnRegisterFailed**                                                      |
   |                       |                                                                                       | -  **CreateTimeout**                                                         |
   |                       |                                                                                       | -  **InitTimeout**                                                           |
   |                       |                                                                                       | -  **RegisterTimeout**                                                       |
   |                       |                                                                                       | -  **InstallTimeout**                                                        |
   |                       |                                                                                       | -  **UpdateTimeout**                                                         |
   |                       |                                                                                       | -  **RollbackTimeout**                                                       |
   |                       |                                                                                       | -  **DeleteTimeout**                                                         |
   |                       |                                                                                       | -  **UnregisterTimeout**                                                     |
   |                       |                                                                                       | -  **Starting**                                                              |
   |                       |                                                                                       | -  **Freezing**                                                              |
   |                       |                                                                                       | -  **Frozen**                                                                |
   |                       |                                                                                       | -  **Restarting**                                                            |
   |                       |                                                                                       | -  **RestartFail**                                                           |
   |                       |                                                                                       | -  **Unhealthy**                                                             |
   |                       |                                                                                       | -  **RestartTimeout**                                                        |
   |                       |                                                                                       | -  **Resizing**                                                              |
   |                       |                                                                                       | -  **ResizeFailed**                                                          |
   |                       |                                                                                       | -  **ResizeTimeout**                                                         |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | instance_status       | Integer                                                                               | Instance status ID:                                                          |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  1: Creating                                                               |
   |                       |                                                                                       | -  2: Created successfully                                                   |
   |                       |                                                                                       | -  3: Creation failed                                                        |
   |                       |                                                                                       | -  4: Initializing                                                           |
   |                       |                                                                                       | -  5: Registering                                                            |
   |                       |                                                                                       | -  6: Running                                                                |
   |                       |                                                                                       | -  7: Initialization failed                                                  |
   |                       |                                                                                       | -  8: Registration failed                                                    |
   |                       |                                                                                       | -  10: Installing                                                            |
   |                       |                                                                                       | -  11: Installation failed                                                   |
   |                       |                                                                                       | -  12: Upgrading                                                             |
   |                       |                                                                                       | -  13: Upgrade failed                                                        |
   |                       |                                                                                       | -  20: Rolling back                                                          |
   |                       |                                                                                       | -  21: Rolled back                                                           |
   |                       |                                                                                       | -  22: Rollback failed                                                       |
   |                       |                                                                                       | -  23: Deleting                                                              |
   |                       |                                                                                       | -  24: Deletion failed                                                       |
   |                       |                                                                                       | -  25: Deregistering                                                         |
   |                       |                                                                                       | -  26: Deregistration failed                                                 |
   |                       |                                                                                       | -  27: Creation timed out                                                    |
   |                       |                                                                                       | -  28: Initialization timed out                                              |
   |                       |                                                                                       | -  29: Registration timed out                                                |
   |                       |                                                                                       | -  30: Installation timed out                                                |
   |                       |                                                                                       | -  31: Upgrade timed out                                                     |
   |                       |                                                                                       | -  32: Rollback timed out                                                    |
   |                       |                                                                                       | -  33: Deletion timed out                                                    |
   |                       |                                                                                       | -  34: Deregistration timed out                                              |
   |                       |                                                                                       | -  35: Starting                                                              |
   |                       |                                                                                       | -  36: Freezing                                                              |
   |                       |                                                                                       | -  37: Frozen                                                                |
   |                       |                                                                                       | -  38: Restarting                                                            |
   |                       |                                                                                       | -  39: Restart failed                                                        |
   |                       |                                                                                       | -  40: Abnormal                                                              |
   |                       |                                                                                       | -  41: Restart timed out                                                     |
   |                       |                                                                                       | -  42: Changing specification                                                |
   |                       |                                                                                       | -  43: Specification change failed                                           |
   |                       |                                                                                       | -  44: Specification change timed out                                        |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | Enumeration values:                                                          |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  **1**                                                                     |
   |                       |                                                                                       | -  **2**                                                                     |
   |                       |                                                                                       | -  **3**                                                                     |
   |                       |                                                                                       | -  **4**                                                                     |
   |                       |                                                                                       | -  **5**                                                                     |
   |                       |                                                                                       | -  **6**                                                                     |
   |                       |                                                                                       | -  **7**                                                                     |
   |                       |                                                                                       | -  **8**                                                                     |
   |                       |                                                                                       | -  **10**                                                                    |
   |                       |                                                                                       | -  **11**                                                                    |
   |                       |                                                                                       | -  **12**                                                                    |
   |                       |                                                                                       | -  **13**                                                                    |
   |                       |                                                                                       | -  **20**                                                                    |
   |                       |                                                                                       | -  **21**                                                                    |
   |                       |                                                                                       | -  **22**                                                                    |
   |                       |                                                                                       | -  **23**                                                                    |
   |                       |                                                                                       | -  **24**                                                                    |
   |                       |                                                                                       | -  **25**                                                                    |
   |                       |                                                                                       | -  **26**                                                                    |
   |                       |                                                                                       | -  **27**                                                                    |
   |                       |                                                                                       | -  **28**                                                                    |
   |                       |                                                                                       | -  **29**                                                                    |
   |                       |                                                                                       | -  **30**                                                                    |
   |                       |                                                                                       | -  **31**                                                                    |
   |                       |                                                                                       | -  **32**                                                                    |
   |                       |                                                                                       | -  **33**                                                                    |
   |                       |                                                                                       | -  **34**                                                                    |
   |                       |                                                                                       | -  **35**                                                                    |
   |                       |                                                                                       | -  **36**                                                                    |
   |                       |                                                                                       | -  **37**                                                                    |
   |                       |                                                                                       | -  **38**                                                                    |
   |                       |                                                                                       | -  **39**                                                                    |
   |                       |                                                                                       | -  **40**                                                                    |
   |                       |                                                                                       | -  **41**                                                                    |
   |                       |                                                                                       | -  **42**                                                                    |
   |                       |                                                                                       | -  **43**                                                                    |
   |                       |                                                                                       | -  **44**                                                                    |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | type                  | String                                                                                | Gateway type.                                                                |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | The default value is apig.                                                   |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | spec                  | String                                                                                | Gateway edition.                                                             |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  BASIC                                                                     |
   |                       |                                                                                       | -  PROFESSIONAL                                                              |
   |                       |                                                                                       | -  ENTERPRISE                                                                |
   |                       |                                                                                       | -  PLATINUM                                                                  |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | Enumeration values:                                                          |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  **BASIC**                                                                 |
   |                       |                                                                                       | -  **PROFESSIONAL**                                                          |
   |                       |                                                                                       | -  **ENTERPRISE**                                                            |
   |                       |                                                                                       | -  **PLATINUM**                                                              |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | create_time           | Long                                                                                  | Time when the gateway is created. The time is in the Unix timestamp format.  |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | enterprise_project_id | String                                                                                | Enterprise project ID. This parameter is required for an enterprise account. |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | eip_address           | String                                                                                | EIP bound to the gateway.                                                    |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | charging_mode         | Integer                                                                               | Billing mode of the gateway.                                                 |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  0: pay-per-use                                                            |
   |                       |                                                                                       | -  1: This parameter is not used currently.                                  |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | Enumeration values:                                                          |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  **0**                                                                     |
   |                       |                                                                                       | -  **1**                                                                     |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | cbc_metadata          | String                                                                                | This parameter is not used currently.                                        |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | loadbalancer_provider | String                                                                                | Type of the load balancer used by the gateway.                               |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  ELB                                                                       |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | Enumeration values:                                                          |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | -  **elb**                                                                   |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+
   | cbc_operation_locks   | Array of :ref:`CbcOperationLock <listinstancesv2__response_cbcoperationlock>` objects | Cloud operations restriction lock.                                           |
   |                       |                                                                                       |                                                                              |
   |                       |                                                                                       | This parameter is not used currently.                                        |
   +-----------------------+---------------------------------------------------------------------------------------+------------------------------------------------------------------------------+

.. _listinstancesv2__response_cbcoperationlock:

.. table:: **Table 6** CbcOperationLock

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================================================================================+
   | lock_scene            | String                | Restriction scenarios:                                                                                                                                                                                           |
   |                       |                       |                                                                                                                                                                                                                  |
   |                       |                       | -  TO_PERIOD_LOCK: Changing the billing mode from pay-per-use to yearly/monthly. In this scenario, deleting resources, changing specifications, and changing from pay-per-use to yearly/monthly are not allowed. |
   |                       |                       | -  SPEC_CHG_LOCK: Changing specifications of the yearly/monthly billing mode. In this scenario, deleting resources and changing specifications are not allowed.                                                  |
   |                       |                       |                                                                                                                                                                                                                  |
   |                       |                       | Enumeration values:                                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                                  |
   |                       |                       | -  **TO_PERIOD_LOCK**                                                                                                                                                                                            |
   |                       |                       | -  **PEC_CHG_LOCK**                                                                                                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lock_source_id        | String                | ID of the object that initiates the restriction                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   ========== ====== ==============

**Status code: 403**

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

None

Example Responses
-----------------

**Status code: 200**

OK

.. code-block::

   {
     "total" : 2,
     "size" : 2,
     "instances" : [ {
       "cbc_metadata" : "CS2006301043A28NF:00301-734023-0--0",
       "charging_mode" : 1,
       "create_time" : 1585302825070,
       "eip_address" : "xxx.xxx.xxx.xxx",
       "enterprise_project_id" : "0",
       "id" : "eddc4d25480b4cd6b512f270a1b8b341",
       "instance_name" : "apig-Enterprise_Project_Pay-per-Use",
       "instance_status" : 6,
       "project_id" : "73d69ae0cfcf460190522d06b60f05ad",
       "spec" : "PROFESSIONAL",
       "status" : "Running",
       "type" : "apig"
     }, {
       "charging_mode" : 0,
       "create_time" : 1594370987422,
       "eip_address" : "xxx.xxx.xxx.xxx",
       "enterprise_project_id" : "0",
       "id" : "2e2d613c64094a4a94ad38e7ca30adee",
       "instance_name" : "apig-autotest-apitest-nodelete",
       "instance_status" : 6,
       "project_id" : "73d69ae0cfcf460190522d06b60f05ad",
       "spec" : "PROFESSIONAL",
       "status" : "Running",
       "type" : "apig",
       "cbc_operation_locks" : [ {
         "lock_scene" : "TO_PERIOD_LOCK",
         "lock_source_id" : "CxxxxxxxxxxxM"
       } ]
     } ]
   }

**Status code: 401**

Unauthorized

.. code-block::

   {
     "error_code" : "APIC.7102",
     "error_msg" : "Incorrect token or token resolution failed"
   }

**Status code: 403**

Forbidden

.. code-block::

   {
     "error_code" : "APIC.7106",
     "error_msg" : "No permissions to request for the method"
   }

**Status code: 500**

Internal Server Error

.. code-block::

   {
     "error_code" : "APIC.9000",
     "error_msg" : "Failed to request internal service"
   }

Status Codes
------------

=========== =====================
Status Code Description
=========== =====================
200         OK
401         Unauthorized
403         Forbidden
500         Internal Server Error
=========== =====================

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
