:original_name: apig_03_0052.html

.. _apig_03_0052:

APIG Operations Recorded by CTS
===============================

Enabling CTS
------------

If you want to collect, record, or query operation logs for APIG in common scenarios such as security analysis, audit, and problem locating, `enable Cloud Trace Service (CTS) <https://docs.otc.t-systems.com/en-us/usermanual/cts/cts_02_0001.html>`__.

CTS provides the following functions:

-  Recording audit logs
-  Querying audit logs
-  Dumping audit logs
-  Encrypting trace files
-  Enabling notifications of key operations

Viewing Key Operations
----------------------

With CTS, you can record operations associated with APIG for future query, audit, and backtracking. The following table lists the APIG operations:

.. table:: **Table 1** APIG operations recorded by CTS

   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Operation                                                        | Resource Type        | Trace Name                        |
   +==================================================================+======================+===================================+
   | Creating an API group                                            | ApiGroup             | createApiGroup                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying an API Group                                           | ApiGroup             | updateApiGroup                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an API group                                            | ApiGroup             | deleteApiGroup                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Verifying an API group name                                      | ApiGroup             | checkApiGroups                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a domain name                                            | ApiGroup             | createDomainBinding               |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Adding a certificate to a domain name                            | ApiGroup             | addDomainCertificate              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a domain name                                          | ApiGroup             | modifySecureTransmission          |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding a domain name                                          | ApiGroup             | relieveDomainBinding              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a domain certificate                                    | ApiGroup             | deleteDomainCertificate           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a response for an API group                             | ApiGroup             | CreateGatewayResponse             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a response of an API group                             | ApiGroup             | UpdateGatewayResponse             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a response of an API group                              | ApiGroup             | DeleteGatewayResponse             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying the response of an error type defined for an API group | ApiGroup             | updateGatewayResponseType         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting the response of an error type defined for an API group  | ApiGroup             | deleteGatewayResponseType         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a domain name with SSL certificates                      | ApiGroup             | AttachDomainCertificate           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding an SSL certificate from a domain name                  | ApiGroup             | DetachDomainCertificate           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating an environment                                          | Environment          | createEnvironment                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying an environment                                         | Environment          | updateEnvironment                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an environment                                          | Environment          | deleteEnvironment                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a variable                                              | EnvVariable          | CreateEnvironmentVariable         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a variable                                              | EnvVariable          | DeleteEnvironmentVariable         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a variable                                             | EnvVariable          | UpdateEnvironmentVariable         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a request throttling policy                             | Throttle             | createThrottle                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a request throttling policy                            | Throttle             | updateThrottle                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a request throttling policy                             | Throttle             | deleteThrottle                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating an API                                                  | Api                  | createApi                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying an API                                                 | Api                  | updateApi                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an API                                                  | Api                  | deleteApi                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Publishing an API or taking an API offline                       | Api                  | CreateOrDeletePublishRecordForApi |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Verifying the API definition                                     | Api                  | checkApis                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Debugging an API                                                 | Api                  | debugApi                          |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Publishing multiple APIs or taking APIs offline                  | Api                  | BatchPublishOrOfflineApi          |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Switching API versions                                           | Api                  | switchApiVersion                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Taking an API version offline                                    | Api                  | offlineApiByVersion               |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a signature key                                         | Signature            | createSignature                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a signature key                                        | Signature            | updateSignature                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a signature key                                         | Signature            | deleteSignature                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a signature key                                          | SignatureBinding     | createSignatureBinding            |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding a signature key                                        | SignatureBinding     | relieveSignatureBinding           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a request throttling policy                              | ThrottleBinding      | createThrottleBinding             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding a request throttling policy                            | ThrottleBinding      | relieveThrottleBinding            |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding multiple request throttling policies                   | ThrottleBinding      | batchRelieveThrottleBinding       |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a special request throttling configuration              | ThrottleSpecial      | createSpecialThrottle             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a special request throttling configuration             | ThrottleSpecial      | updateSpecialThrottle             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an excluded request throttling configuration            | ThrottleSpecial      | deleteSpecialThrottle             |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Authorizing apps                                                 | AppAuth              | grantAuth                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Canceling authorization                                          | AppAuth              | relieveAuth                       |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating an access control policy                                | Acl                  | createAcl                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying an access control policy                               | Acl                  | updateAcl                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an access control policy                                | Acl                  | deleteAcl                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting multiple access control policies                        | Acl                  | batchDeleteAcl                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding an access control policy to an API                       | AclBinding           | createAclBinding                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding an access control policy from an API                   | AclBinding           | relieveAclBinding                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding multiple access control policies from APIs             | AclBinding           | batchRelieveAclBinding            |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a custom authorizer                                     | Authorizer           | createAuthorizer                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a custom authorizer                                    | Authorizer           | updateAuthorizer                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a custom authorizer                                     | Authorizer           | deleteAuthorizer                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Exporting APIs                                                   | Swagger              | ExportApiDefinitions              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Importing APIs                                                   | Swagger              | swaggerImportApiToGroup           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a VPC channel                                           | Vpc                  | createVpc                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Updating a VPC channel                                           | Vpc                  | updateVpc                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a VPC channel                                           | Vpc                  | deleteVpc                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Adding or updating backend instances                             | Vpc                  | addVpcMember                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Updating backend instances                                       | Vpc                  | putVpcMember                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Removing a backend server                                        | Vpc                  | deleteVpcMember                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Enabling backend servers                                         | Vpc                  | BatchEnableMembers                |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Disabling backend servers                                        | Vpc                  | BatchDisableMembers               |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying VPC channel health check                               | Vpc                  | UpdateHealthCheck                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Adding or updating a backend server group of a VPC channel       | Vpc                  | createVpcMemberGroup              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a backend server group of a VPC channel                 | Vpc                  | deleteVpcMemberGroup              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Updating a Backend Server Group of a VPC Channel                 | Vpc                  | updateVpcMemberGroup              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Configuring a feature for a gateway                              | Feature              | CreateFeatureV2                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a dedicated gateway (Pay-per-use)                       | Instance             | createInstance                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Updating a dedicated gateway                                     | Instance             | modifyInstance                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding an EIP to a gateway or updating the EIP of a gateway     | eip                  | updateInstanceEip                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding the EIP of a gateway                                   | eip                  | deleteInstanceEip                 |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Enabling public outbound access for a gateway                    | nat-eip              | openEgressEip                     |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Updating the public outbound access bandwidth of a gateway       | nat-eip              | updateNatEipBandwidthSize         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Disabling public outbound access for a gateway                   | nat-eip              | closeEgressEip                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Enabling public inbound access                                   | ingress-eip          | openIngressEip                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Updating the public inbound access bandwidth of a gateway        | ingress-eip          | modifyIngressEip                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Disabling public inbound access for a gateway                    | ingress-eip          | deleteIngressEip                  |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a dedicated gateway                                     | Instance             | deleteInstance                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying the specifications of a pay-per-use gateway            | Instance             | resizePostpaidInstance            |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Batch adding or deleting gateway tags                            | Instance             | updateInstanceTags                |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Adding a custom inbound port for a gateway                       | custom-ingress-ports | AddCustomIngressPort              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a custom inbound port specified for a gateway           | custom-ingress-ports | DeleteCustomIngressPort           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Accepting or rejecting a VPC endpoint connection                 | vpc-endpoint         | acceptOrRejectConnections         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Adding whitelist records for a VPC endpoint service              | vpc-endpoint         | addVpcEndpointPermissions         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting whitelist records of a VPC endpoint service             | vpc-endpoint         | removeVpcEndpointPermissions      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Importing a microservice                                         | Microservice         | importMicroservice                |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Adding an SSL certificate                                        | SslCertificate       | createSslCertificate              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an SSL certificate                                      | SslCertificate       | deleteSslCertificate              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying an SSL certificate                                     | SslCertificate       | updateSslCertificate              |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding an SSL certificate to a domain name                      | Certificate          | sslBatchAssociateDomains          |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding an SSL certificate from a domain name                  | Certificate          | sslBatchDisassociateDomains       |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a plug-in                                               | Plugin               | CreatePlugin                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a plug-in                                              | Plugin               | UpdatePlugin                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a plug-in                                               | Plugin               | DeletePlugin                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a plug-in to an API                                      | Plugin               | pluginAttachApi                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a plug-in to an API                                      | Plugin               | apiAttachPlugin                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding an API from a plug-in                                  | Plugin               | pluginDetachApi                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding a plug-in from an API                                  | Plugin               | apiDetachPlugin                   |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating an app                                                  | App                  | createApp                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying an app                                                 | App                  | UpdateApp                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an app                                                  | App                  | deleteApp                         |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Resetting an AppSecret                                           | App                  | resetAppSecret                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Verifying an app                                                 | App                  | CheckApp                          |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating an AppCode                                              | AppCode              | CreateAppCode                     |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Generating an AppCode                                            | AppCode              | createWithRandomAppCode           |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting an AppCode                                              | AppCode              | DeleteAppCode                     |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Configuring access control settings for an app                   | AppAcl               | UpdateAppAcl                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting access control settings of an app                       | AppAcl               | DeleteAppAcl                      |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Creating a credential quota                                      | AppQuota             | CreateAppQuota                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Modifying a credential quota                                     | AppQuota             | UpdateAppQuota                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Deleting a credential quota                                      | AppQuota             | DeleteAppQuota                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Binding a credential quota with credentials                      | AppQuotaBinding      | AssociateAppsForAppQuota          |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Unbinding a credential quota from a credential                   | AppQuotaBinding      | DisassociateAppQuotaWithApp       |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Exporting APIs asynchronously                                    | Async                | asyncExportApi                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+
   | Importing APIs asynchronously                                    | Async                | asyncImportApi                    |
   +------------------------------------------------------------------+----------------------+-----------------------------------+

Disabling CTS
-------------

Disable CTS by following the procedure in section "Deleting a Tracker" in the *Cloud Trace Service User Guide*.
