:original_name: apig-faq-2005010.html

.. _apig-faq-2005010:

What Are the Possible Causes for an API Calling Failure?
========================================================

Network
-------

API calling failures may occur in three scenarios: within a VPC, between VPCs, and on a public network.

-  Within a VPC: Check whether the domain name is the same as that automatically allocated for the API.

-  Between VPCs: Check whether the two VPCs are connected. If they are not connected, create a VPC peering connection to connect the two VPCs.

   For details about how to create and use VPC peering connections, see section "VPC Peering Connection" in the *Virtual Private Cloud User Guide*.

-  On a public network:

   -  The API is not bound with an EIP and does not have a valid address for public network access.

      Bind an EIP to the API and try again. For details, see section "Creating a Gateway" in the *API Gateway User Guide*.

   -  The inbound rules are incorrectly configured.

      For details about how to configure inbound rules, see section "Creating a Gateway" in the *API Gateway User Guide*.

   -  The request header "host:*Group domain name*" is not added when you call the API. Add the request header and try again.

Domain Name
-----------

-  Check whether the domain name bound to the API group to which the API belongs has been successfully licensed and can be resolved.
-  Check whether the domain name has been bound to the correct API group.
-  The subdomain name (debugging domain name) automatically allocated to the API group is accessed too many times. The subdomain name can be accessed only 1000 times a day. It is unique and cannot be modified. Add independent domain names for the group to make the APIs in the group accessible.

API Publishing
--------------

Check whether the API has been published. If the API has been modified, publish it again. If the API has been published to a non-RELEASE environment, specify the **X-Stage** header as the environment name.

API Authentication
------------------

If the API uses app authentication, check whether the AppKey and AppSecret used to call the API are correct.

API Control Policies
--------------------

-  Check whether the access control policy bound to the API is correct.
-  Check whether the request throttling limit of the API has been reached. If no request throttling policy is created for an API, the API can be accessed 200 times per second by default. To change this limit of dedicated gateways, go to the **Gateway Information** page, click the **Parameters** tab, and modify the **ratelimit_api_limits** parameter.
