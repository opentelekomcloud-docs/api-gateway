:original_name: apig-api-190529268.html

.. _apig-api-190529268:

Authentication
==============

Requests for calling an API can be authenticated using either of the following methods:

-  AK/SK-based authentication: Requests are authenticated by encrypting the request body using an AK/SK pair. AK/SK-based authentication is recommended because it provides higher security than token-based authentication.

-  Token-based authentication: Requests are authenticated using a token.

.. _apig-api-190529268__en-us_topic_0172440411_en-us_topic_0121671869_section0390282152:

AK/SK-based Authentication
--------------------------

An AK/SK is used to verify the identity of a request sender. In AK/SK-based authentication, a signature needs to be obtained and then added to requests.

-  AK: access key ID, which is a unique identifier used with a secret access key to sign requests cryptographically.
-  SK: secret access key used in conjunction with an AK to sign requests cryptographically. It identifies a request sender and prevents the request from being modified.

The following uses a demo project to show how to sign a request and use an HTTP client to send an HTTPS request.

Download the demo project at https://github.com/api-gate-way/SdkDemo.

If you do not need the demo, obtain the APIG signing SDK from technical support personnel.

Decompress the downloaded package and reference the obtained JAR file as a dependency.


.. figure:: /_static/images/en-us_image_0000002155592541.png
   :alt: **Figure 1** Adding the APIG signing SDK

   **Figure 1** Adding the APIG signing SDK

#. Generate an AK/SK. (If an AK/SK file has already been obtained, skip this step and locate the downloaded AK/SK file. Generally, the file name will be **credentials.csv**.)

   a. Register an account and log in to the management console.
   b. Hover over the username and choose **My Credentials** from the drop-down list.

   c. Choose **Access Keys** from the navigation pane.
   d. Click **Create Access Key**.
   e. Enter the login password.
   f. Enter the verification code received by email or SMS message.

      .. note::

         For users created in IAM that have not bound any email address or mobile number, only the login password needs to be entered.

   g. Click **OK** to download the access key. **Keep the access key secure.**

#. Download and decompress the demo project.

#. .. _apig-api-190529268__en-us_topic_0172440411_en-us_topic_0121671869_li19564155663214:

   Import the demo project to Eclipse.


   .. figure:: /_static/images/en-us_image_0000002120352414.png
      :alt: **Figure 2** Selecting Existing Projects into Workspace

      **Figure 2** Selecting Existing Projects into Workspace


   .. figure:: /_static/images/en-us_image_0000002120194306.png
      :alt: **Figure 3** Selecting the demo project

      **Figure 3** Selecting the demo project


   .. figure:: /_static/images/en-us_image_0000002155714161.png
      :alt: **Figure 4** Structure of the demo project

      **Figure 4** Structure of the demo project

#. Sign the request.

   The request signing method is integrated in the JAR files imported in :ref:`3 <apig-api-190529268__en-us_topic_0172440411_en-us_topic_0121671869_li19564155663214>`. The request needs to be signed before it is sent. The signature will then be added as part of the HTTP header to the request.

   The demo code is classified into the following classes to demonstrate signing and sending the HTTP request:

   -  **AccessService**: an abstract class that merges the GET, POST, PUT, and DELETE methods into the access method.
   -  **Demo**: Execution entry used to simulate the sending of GET, POST, PUT, and DELETE requests.
   -  **AccessServiceImpl**: Implements the access method, which contains the code required for communication with APIG.

   a. Edit the main() method in the **Demo.java** file, and replace the bold text with actual values.

      As shown in the following code, if you use other methods such as POST, PUT, and DELETE, see the corresponding comment.

      Specify **region**, **serviceName**, **ak/sk**, and **url** as the actual values. In this demo, the URLs for accessing VPC resources are used.

      To obtain the project ID in the URLs, see :ref:`Obtaining a Project ID <apig-api-180713009>`. To obtain the endpoint, contact the enterprise administrator.

      .. code-block::

         //TODO: Replace region with the name of the region in which the service to be accessed is located.
         private static final String region = "";

         //TODO: Replace vpc with the name of the service you want to access. For example, ecs, vpc, iam, and elb.
         private static final String serviceName = "";

         public static void main(String[] args) throws UnsupportedEncodingException
         {
         //TODO: Replace the AK and SK with those obtained on the My Credential page.
         String ak = "ZIRRKMTWP******1WKNKB";
         String sk = "Us0mdMNHk******YrRCnW0ecfzl";

         //TODO: To specify a project ID (multi-project scenarios), add the X-Project-Id header.
         //TODO: To access a global service, such as IAM, DNS, CDN, and TMS, add the X-Domain-Id header to specify an account ID.
         //TODO: To add a header, find "Add special headers" in the AccessServiceImple.java file.

         //TODO: Test the API
         String url = "https://{Endpoint}/v1/{project_id}/vpcs";
         get(ak, sk, url);

         //TODO: When creating a VPC, replace {project_id} in postUrl with the actual value.
         //String postUrl = "https://serviceEndpoint/v1/{project_id}/cloudservers";
         //String postbody ="{\"vpc\": {\"name\": \"vpc\",\"cidr\": \"192.168.0.0/16\"}}";
         //post(ak, sk, postUrl, postbody);

         //TODO: When querying a VPC, replace {project_id} in url with the actual value.
         //String url = "https://serviceEndpoint/v1/{project_id}/vpcs/{vpc_id}";
         //get(ak, sk, url);

         //TODO: When updating a VPC, replace {project_id} and {vpc_id} in putUrl with the actual values.
         //String putUrl = "https://serviceEndpoint/v1/{project_id}/vpcs/{vpc_id}";
         //String putbody ="{\"vpc\":{\"name\": \"vpc1\",\"cidr\": \"192.168.0.0/16\"}}";
         //put(ak, sk, putUrl, putbody);

         //TODO: When deleting a VPC, replace {project_id} and {vpc_id} in deleteUrl with the actual values.
         //String deleteUrl = "https://serviceEndpoint/v1/{project_id}/vpcs/{vpc_id}";
         //delete(ak, sk, deleteUrl);
         }

   b. Compile the code and call the API.

      In the **Package Explorer** area on the left, right-click **Demo.java**, choose **Run AS** > **Java Application** from the shortcut menu to run the demo code.

      You can view the API call logs on the console.

Token-based Authentication
--------------------------

.. important::

   -  The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.
   -  Ensure that the token is valid when you use it. Using a token that will soon expire may cause API calling failures.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API.

When calling an API to obtain a user token, you must set **auth.scope** in the request body to **project**.

.. code-block::

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxx"
               }
           }
       }
   }

After a token is obtained, the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFG....**, **X-Auth-Token: ABCDEFG....** can be added to a request as follows:

.. code-block::

   POST https://{apig_endpoint}/v2/{project_id}/v2/{project_id}/apigw/instances/{instance_id}/api-groups
   Content-Type: application/json
   X-Auth-Token: ABCDEFG....
