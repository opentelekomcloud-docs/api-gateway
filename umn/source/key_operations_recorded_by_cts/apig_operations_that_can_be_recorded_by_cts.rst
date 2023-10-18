:original_name: apig-en-ug-180307058.html

.. _apig-en-ug-180307058:

APIG operations that can be recorded by CTS
===========================================

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

.. table:: **Table 1** APIG operations that can be recorded by CTS

   +-------------------------------------------------------+------------------+------------------------------+
   | Operation                                             | Resource Type    | Trace Name                   |
   +=======================================================+==================+==============================+
   | Creating an API group                                 | ApiGroup         | createApiGroup               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an API group                                 | ApiGroup         | deleteApiGroup               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an API group                                 | ApiGroup         | updateApiGroup               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding a domain name                                 | ApiGroup         | createDomainBinding          |
   +-------------------------------------------------------+------------------+------------------------------+
   | Change minimum TLS version                            | ApiGroup         | modifySecureTransmission     |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding a domain name                               | ApiGroup         | relieveDomainBinding         |
   +-------------------------------------------------------+------------------+------------------------------+
   | Adding a domain certificate                           | ApiGroup         | addDomainCertificate         |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting a domain certificate                         | ApiGroup         | deleteDomainCertificate      |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an API                                       | Api              | createApi                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an API                                       | Api              | deleteApi                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting multiple APIs                                | Api              | batchDeleteApi               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an API                                       | Api              | updateApi                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Publishing an API                                     | Api              | publishApi                   |
   +-------------------------------------------------------+------------------+------------------------------+
   | Taking an API offline                                 | Api              | offlineApi                   |
   +-------------------------------------------------------+------------------+------------------------------+
   | Publishing multiple APIs or taking APIs offline       | Api              | batchPublishOrOfflineApi     |
   +-------------------------------------------------------+------------------+------------------------------+
   | Switching API versions                                | Api              | switchApiVersion             |
   +-------------------------------------------------------+------------------+------------------------------+
   | Taking an API version offline                         | Api              | offlineApiByVersion          |
   +-------------------------------------------------------+------------------+------------------------------+
   | Debugging an API                                      | Api              | debugApi                     |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an environment                               | Environment      | createEnvironment            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an environment                               | Environment      | deleteEnvironment            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an environment                               | Environment      | updateEnvironment            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an environment variable                      | EnvVariable      | createEnvVariable            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an environment variable                      | EnvVariable      | updateEnvVariable            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an environment variable                      | EnvVariable      | deleteEnvVariable            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an app                                       | App              | createApp                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an app                                       | App              | deleteApp                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an application                               | App              | updateApp                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Resetting AppSecret                                   | App              | resetAppSecret               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding a client to an API                            | AppAuth          | grantAuth                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding a client from an API                        | AppAuth          | relieveAuth                  |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating a signature key                              | Signature        | createSignature              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting a signature key                              | Signature        | deleteSignature              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating a signature key                              | Signature        | updateSignature              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding a signature key                               | SignatureBinding | createSignatureBinding       |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding a signature key                             | SignatureBinding | relieveSignatureBinding      |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an access control policy                     | Acl              | createAcl                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an access control policy                     | Acl              | deleteAcl                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting access control policies                      | Acl              | batchDeleteAcl               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an access control policy                     | Acl              | updateAcl                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an access control blacklist                  | Acl              | addAclValue                  |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an access control blacklist                  | Acl              | deleteAclValue               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding an access control policy to an API            | AclBinding       | createAclBinding             |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding an access control policy from an API        | AclBinding       | relieveAclBinding            |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding multiple access control policies from APIs  | AclBinding       | batchRelieveAclBinding       |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating a request throttling policy                  | Throttle         | createThrottle               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting a request throttling policy                  | Throttle         | deleteThrottle               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting multiple request throttling policies         | Throttle         | batchDeleteThrottle          |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating a requesting throttling policy               | Throttle         | updateThrottle               |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding a request throttling policy                   | ThrottleBinding  | createThrottleBinding        |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding a request throttling policy                 | ThrottleBinding  | relieveThrottleBinding       |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding multiple request throttling policies        | ThrottleBinding  | batchRelieveThrottleBinding  |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating an excluded request throttling configuration | ThrottleSpecial  | createSpecialThrottle        |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting an excluded request throttling configuration | ThrottleSpecial  | deleteSpecialThrottle        |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating an excluded request throttling configuration | ThrottleSpecial  | updateSpecialThrottle        |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating a load balance channel                       | Vpc              | createVpc                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting a load balance channel                       | Vpc              | deleteVpc                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating a load balance channel                       | Vpc              | updateVpc                    |
   +-------------------------------------------------------+------------------+------------------------------+
   | Adding members to a load balance channel              | Vpc              | addVpcMember                 |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting members from a load balance channel          | Vpc              | deleteVpcMember              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Exporting an API                                      | Swagger          | swaggerExportApi             |
   +-------------------------------------------------------+------------------+------------------------------+
   | Exporting multiple APIs                               | Swagger          | swaggerExportApiList         |
   +-------------------------------------------------------+------------------+------------------------------+
   | Exporting all APIs in a group                         | Swagger          | swaggerExportApiByGroup      |
   +-------------------------------------------------------+------------------+------------------------------+
   | Importing APIs to a new group                         | Swagger          | swaggerImportApiToNewGroup   |
   +-------------------------------------------------------+------------------+------------------------------+
   | Importing APIs to an existing group                   | Swagger          | swaggerImportApiToExistGroup |
   +-------------------------------------------------------+------------------+------------------------------+
   | Exporting all custom backends                         | Swagger          | SwaggerExportLdApi           |
   +-------------------------------------------------------+------------------+------------------------------+
   | Importing custom backends                             | Swagger          | SwaggerImportLdApi           |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating a custom authorizer                          | Authorizer       | createAuthorizer             |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting a custom authorizer                          | Authorizer       | deleteAuthorizer             |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating a custom authorizer                          | Authorizer       | updateAuthorizer             |
   +-------------------------------------------------------+------------------+------------------------------+
   | Creating a plug-in                                    | Plugin           | createPlugin                 |
   +-------------------------------------------------------+------------------+------------------------------+
   | Updating a plug-in                                    | Plugin           | updatePlugin                 |
   +-------------------------------------------------------+------------------+------------------------------+
   | Deleting a plug-in                                    | Plugin           | deletePlugin                 |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding a plug-in to an API                           | Plugin           | pluginAttachApi              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding an API from a plug-in                       | Plugin           | pluginDetachApi              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Binding a plug-in to an API                           | Plugin           | apiAttachPlugin              |
   +-------------------------------------------------------+------------------+------------------------------+
   | Unbinding a plug-in from an API                       | Plugin           | apiDetachPlugin              |
   +-------------------------------------------------------+------------------+------------------------------+

Disabling CTS
-------------

Disable CTS by following the procedure in section "Deleting a Tracker" in the *Cloud Trace Service User Guide*.
