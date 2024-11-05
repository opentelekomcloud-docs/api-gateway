:original_name: apig_03_0052.html

.. _apig_03_0052:

APIG Operations Recorded by CTS
===============================

Enabling CTS
------------

If you want to collect, record, or query operation logs for APIG in common scenarios such as security analysis, audit, and problem locating, enable Cloud Trace Service (CTS). For details, see section "Enabling CTS" in the *Cloud Trace Service User Guide*.

CTS provides the following functions:

-  Recording audit logs
-  Querying audit logs
-  Dumping audit logs
-  Encrypting trace files
-  Enabling notifications of key operations

Viewing Key Operations
----------------------

With CTS, you can record operations associated with APIG for future query, audit, and backtracking.

.. table:: **Table 1** APIG operations recorded by CTS

   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Operation                                                        | Resource Type    | Trace Name                           |
   +==================================================================+==================+======================================+
   | Creating an API group                                            | ApiGroup         | createApiGroup                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying an API Group                                           | ApiGroup         | updateApiGroup                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an API group                                            | ApiGroup         | deleteApiGroup                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Verifying an API group name                                      | Swagger          | CheckApiGroups                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating an environment                                          | Environment      | createEnvironment                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying an environment                                         | Environment      | updateEnvironment                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an environment                                          | Environment      | deleteEnvironment                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a variable                                              | EnvVariable      | CreateEnvironmentVariable            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a variable                                              | EnvVariable      | DeleteEnvironmentVariable            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a variable                                             | EnvVariable      | UpdateEnvironmentVariable            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a request throttling policy                             | Throttle         | CreateRequestThrottlingPolicy        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a request throttling policy                            | Throttle         | UpdateRequestThrottlingPolicy        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a request throttling policy                             | Throttle         | DeleteRequestThrottlingPolicy        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating an API                                                  | Api              | CreateApi                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying an API                                                 | Api              | UpdateApi                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an API                                                  | Api              | DeleteApi                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Publishing an API or taking an API offline                       | Api              | CreateOrDeletePublishRecordForApi    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Verifying the API definition                                     | Api              | CheckApis                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Debugging an API                                                 | Api              | DebugApi                             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Publishing multiple APIs or taking APIs offline                  | Api              | BatchPublishOrOfflineApi             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Switching API versions                                           | Api              | ChangeApiVersion                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Taking an API version offline                                    | Api              | DeleteApiByVersionId                 |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a signature key                                         | Signature        | CreateSignatureKey                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a signature key                                        | Signature        | UpdateSignatureKey                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a signature key                                         | Signature        | DeleteSignatureKey                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a signature key                                          | SignatureBinding | AssociateSignatureKey                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding a signature key                                        | SignatureBinding | DisassociateSignatureKey             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a request throttling policy                              | ThrottleBinding  | AssociateRequestThrottlingPolicy     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding a request throttling policy                            | ThrottleBinding  | DisassociateRequestThrottlingPolicy  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding multiple request throttling policies                   | ThrottleBinding  | BatchDisassociateThrottlingPolicy    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a special request throttling configuration              | ThrottleSpecial  | CreateSpecialThrottlingConfiguration |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a special request throttling configuration             | ThrottleSpecial  | UpdateSpecialThrottlingConfiguration |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an excluded request throttling configuration            | ThrottleSpecial  | DeleteSpecialThrottlingConfiguration |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Authorizing apps                                                 | AppAuth          | CreateAuthorizingApps                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Canceling authorization                                          | AppAuth          | CancelingAuthorization               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a domain name                                            | ApiGroup         | AssociateDomain                      |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Adding a certificate to a domain name                            | ApiGroup         | AssociateCertificate                 |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a domain name                                          | ApiGroup         | UpdateDomain                         |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding a domain name                                          | ApiGroup         | DisassociateDomain                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a domain certificate                                    | ApiGroup         | DisassociateCertificate              |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating an access control policy                                | Acl              | CreateAclStrategy                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying an access control policy                               | Acl              | UpdateAclStrategy                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an access control policy                                | Acl              | DeleteAcl                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting multiple access control policies                        | Acl              | BatchDeleteAclV2                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding an access control policy to an API                       | AclBinding       | CreateApiAclBinding                  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding an access control policy from an API                   | AclBinding       | DeleteApiAclBinding                  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding multiple access control policies from APIs             | AclBinding       | BatchDeleteApiAclBinding             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a custom authorizer                                     | Authorizer       | CreateCustomAuthorizer               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a custom authorizer                                    | Authorizer       | UpdateCustomAuthorizer               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a custom authorizer                                     | Authorizer       | DeleteCustomAuthorizer               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Exporting APIs                                                   | Swagger          | ExportApiDefinitions                 |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Importing APIs                                                   | Swagger          | ImportApiDefinitions                 |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a VPC channel                                           | Vpc              | CreateVpcChannel                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Updating a VPC channel                                           | Vpc              | UpdateVpcChannel                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a VPC channel                                           | Vpc              | DeleteVpcChannel                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Adding or updating backend instances                             | Vpc              | AddingBackendInstances               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Updating backend instances                                       | Vpc              | UpdateBackendInstances               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Removing a backend server                                        | Vpc              | DeleteBackendInstance                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Enabling backend servers                                         | Vpc              | BatchEnableMembers                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Disabling backend servers                                        | Vpc              | BatchDisableMembers                  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying VPC channel health check                               | Vpc              | UpdateHealthCheck                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Adding or updating a backend server group of a VPC channel       | Vpc              | CreateMemberGroup                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a backend server group of a VPC channel                 | Vpc              | DeleteMemberGroup                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Updating a Backend Server Group of a VPC Channel                 | Vpc              | UpdateMemberGroup                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a response for an API group                             | ApiGroup         | CreateGatewayResponse                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a response of an API group                             | ApiGroup         | UpdateGatewayResponse                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a response of an API group                              | ApiGroup         | DeleteGatewayResponse                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying the response of an error type defined for an API group | ApiGroup         | UpdateGatewayResponseType            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting the response of an error type defined for an API group  | ApiGroup         | DeleteGatewayResponseType            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Configuring a feature for a gateway                              | Feature          | CreateFeatureV2                      |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a dedicated gateway (Pay-per-use)                       | Instance         | CreateInstance                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Updating a dedicated gateway                                     | Instance         | UpdateInstance                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding an EIP to a gateway or updating the EIP of a gateway     | Instance         | AddEip                               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding the EIP of a gateway                                   | Instance         | RemoveEip                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Enabling public outbound access for a gateway                    | Instance         | AddEngressEip                        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Updating the public outbound access bandwidth of a gateway       | Instance         | UpdateEngressEip                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Disabling public outbound access for a gateway                   | Instance         | RemoveEngressEip                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Enabling public inbound access                                   | Instance         | AddIngressEip                        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Updating the public inbound access bandwidth of a gateway        | Instance         | UpdateIngressEip                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Disabling public inbound access for a gateway                    | Instance         | RemoveIngressEip                     |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a dedicated gateway                                     | Instance         | DeleteInstances                      |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying the specifications of a pay-per-use gateway            | Instance         | CreatePostPayResizeOrder             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Accepting or rejecting a VPC endpoint connection                 | vpc-endpoint     | AcceptOrRejectEndpointConnections    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Adding whitelist records for a VPC endpoint service              | vpc-endpoint     | AddEndpointPermissions               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting whitelist records of a VPC endpoint service             | vpc-endpoint     | DeleteEndpointPermissions            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Batch adding or deleting gateway tags                            | Instance         | BatchCreateOrDeleteInstanceTags      |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Importing a microservice                                         | Microservice     | ImportMicroservice                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Adding an SSL certificate                                        | SslCertificate   | CreateCertificate                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a domain name with SSL certificates                      | ApiGroup         | BatchAssociateCerts                  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding the SSL certificates of a domain name                  | ApiGroup         | BatchDisassociateCerts               |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an SSL certificate                                      | SslCertificate   | DeleteCertificate                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying an SSL certificate                                     | SslCertificate   | UpdateCertificate                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding an SSL certificate to a domain name                      | Certificate      | BatchAssociateDomains                |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding an SSL certificate from a domain name                  | Certificate      | BatchDisassociateDomains             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a plug-in                                               | Plugin           | CreatePlugin                         |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a plug-in                                              | Plugin           | UpdatePlugin                         |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a plug-in                                               | Plugin           | DeletePlugin                         |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a plug-in to an API                                      | Plugin           | AttachApiToPlugin                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a plug-in to an API                                      | Plugin           | AttachPluginToApi                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding an API from a plug-in                                  | Plugin           | DetachApiFromPlugin                  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding a plug-in from an API                                  | Plugin           | DetachPluginFromApi                  |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating an app                                                  | App              | CreateAnApp                          |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying an app                                                 | App              | UpdateApp                            |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an app                                                  | App              | DeleteAppV2                          |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Resetting an Appsecret                                           | App              | ResettingAppSecret                   |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Verifying an app                                                 | App              | CheckApp                             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating an AppCode                                              | AppCode          | CreateAppCode                        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Generating an AppCode                                            | AppCode          | CreateAppCodeAuto                    |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting an AppCode                                              | AppCode          | DeleteAppCode                        |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Configuring access control settings for an app                   | AppAcl           | UpdateAppAcl                         |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting access control settings of an app                       | AppAcl           | DeleteAppAcl                         |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Creating a credential quota                                      | AppQuota         | CreateAppQuota                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Modifying a credential quota                                     | AppQuota         | UpdateAppQuota                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Deleting a credential quota                                      | AppQuota         | DeleteAppQuota                       |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Binding a credential quota with credentials                      | AppQuotaBinding  | AssociateAppsForAppQuota             |
   +------------------------------------------------------------------+------------------+--------------------------------------+
   | Unbinding a credential quota from a credential                   | AppQuotaBinding  | DisassociateAppQuotaWithApp          |
   +------------------------------------------------------------------+------------------+--------------------------------------+

Disabling CTS
-------------

Disable CTS by following the procedure in section "Deleting a Tracker" in the *Cloud Trace Service User Guide*.
