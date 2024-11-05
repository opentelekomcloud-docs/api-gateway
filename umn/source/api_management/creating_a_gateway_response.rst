:original_name: apig_03_0008.html

.. _apig_03_0008:

Creating a Gateway Response
===========================

A gateway response is displayed if APIG fails to process an API request. APIG provides a set of default responses and also allows you to create responses with custom status codes and content. The response content must be in JSON format.

For example, the content of a default gateway response is as follows:

.. code-block::

   {"error_code": "$context.error.code", "error_msg": "$context.error.message", "request_id": "$context.requestId"}

You can add a response with the following content:

.. code-block::

   {"errorcode": "$context.error.code", "errormsg": "$context.error.message", "requestid": "$context.requestId","apiId":"$context.apiId"}

You can add more fields to or delete existing fields from the JSON body.

.. note::

   -  You can create a maximum of four gateway responses for each group.
   -  A maximum of 10 response headers can be customized. The key of a response header can contain 1 to 128 characters, including digits, letters, and underscores (_). The value can reference runtime variables (see :ref:`Context Variables <apig_03_0008__en-us_topic_0000001221774147_en-us_topic_0226843033_section0417113411215>`), but cannot contain double brackets ([[ or ]]).
   -  The type of a default or custom response cannot be modified, but the status code and content of the response can.
   -  The type of a gateway response cannot be changed. For details, see :ref:`Response Types <apig_03_0008__en-us_topic_0000001221774147_en-us_topic_0226843033_section188951150101>`.
   -  Gateway responses can contain the API gateway context variables (starting with **$context**). For details, see :ref:`Context Variables <apig_03_0008__en-us_topic_0000001221774147_en-us_topic_0226843033_section0417113411215>`.

Procedure
---------

#. Go to the APIG console.

2. Select a dedicated gateway at the top of the navigation pane.

3. Choose **API Management** > **API Groups**.

4. Click a group name.

5. Click the **Group Information** tab.

6. In the **Gateway Responses** area, create or modify gateway responses.

   To cancel modifications to a default response, click **Restore Defaults** in the upper right.

.. _apig_03_0008__en-us_topic_0000001221774147_en-us_topic_0226843033_section188951150101:

Response Types
--------------

The following table lists the response types supported by APIG. You can define status codes to meet your service requirements.

.. table:: **Table 1** Error response types supported by APIG

   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Response Name                         | Default Status Code | Description                                                                                                       |
   +=======================================+=====================+===================================================================================================================+
   | Access Denied                         | 403                 | Access denied. For example, the access control policy is triggered or an attack is detected.                      |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Authorizer Configuration Error        | 500                 | A custom authorizer error has occurred. For example, communication failed or an error response was returned.      |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Authorizer Failed                     | 500                 | The custom authorization failed.                                                                                  |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Incorrect Identity Source             | 401                 | The identity source of the custom authorizer is missing or invalid.                                               |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Third-Party Configuration Error       | 500                 | A third-party authorizer error has occurred. For example, communication failed or an error response was returned. |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Third-Party Authorizer Failure        | 401                 | The third-party authorizer returns an authentication failure.                                                     |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Incorrect Third-Party Identity Source | 401                 | The identity source of the third-party authorizer is missing.                                                     |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Authentication Failure                | 401                 | IAM or app authentication failed.                                                                                 |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Identity Source Not Found             | 401                 | No identity source has been specified.                                                                            |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Backend Timeout                       | 504                 | Communication with the backend service timed out.                                                                 |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Backend Unavailable                   | 502                 | The backend service is unavailable due to communication error.                                                    |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Default 4XX                           | ``-``               | Another 4XX error occurred.                                                                                       |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Default 5XX                           | ``-``               | Another 5XX error occurred.                                                                                       |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | No API Found                          | 404                 | No API is found.                                                                                                  |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Incorrect Request Parameters          | 400                 | The request parameters are incorrect or the HTTP method is not supported.                                         |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Request Throttled                     | 429                 | The request was rejected due to request throttling.                                                               |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+
   | Unauthorized Credential               | 401                 | The credential you are using has not been authorized to call the API.                                             |
   +---------------------------------------+---------------------+-------------------------------------------------------------------------------------------------------------------+

.. _apig_03_0008__en-us_topic_0000001221774147_en-us_topic_0226843033_section0417113411215:

Context Variables
-----------------

.. table:: **Table 2** Variables that can be used in response message body

   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Variable                              | Description                                                                                                    |
   +=======================================+================================================================================================================+
   | $context.apiId                        | API ID.                                                                                                        |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.apiName                      | API name.                                                                                                      |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.appId                        | ID of the credential that calls the API.                                                                       |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.appName                      | Name of the credential that calls the API.                                                                     |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.requestId                    | Request ID generated when the API is called.                                                                   |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.stage                        | Deployment environment in which the API is called.                                                             |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.sourceIp                     | Source IP address of the API caller.                                                                           |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.reqPath                      | API request path, excluding the query string.                                                                  |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.reqUri                       | API request path, including the query string.                                                                  |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.reqMethod                    | Request method.                                                                                                |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.authorizer.frontend.property | Values of the specified attribute-value pairs mapped to the context in the frontend custom authorizer response |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.authorizer.backend.property  | Values of the specified attribute-value pairs mapped to the context in the backend custom authorizer response  |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.error.message                | Error message.                                                                                                 |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.error.code                   | Error code.                                                                                                    |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.error.type                   | Error type.                                                                                                    |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
