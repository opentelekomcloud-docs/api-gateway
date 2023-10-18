:original_name: apig-lgug-200226001.html

.. _apig-lgug-200226001:

Adding a Gateway Response
=========================

Scenario
--------

A gateway response is displayed if APIG fails to process an API request. APIG provides a set of default responses and also allows you to create gateway responses with custom status codes and content, on the **API Groups** page. The response content must be in JSON format.

For example, the content of a default gateway response is as follows:

.. code-block::

   {"error_code": "$context.error.code", "error_msg": "$context.error.message", "request_id": "$context.requestId"}

You can add a response with the following content:

.. code-block::

   {"errorcode": "$context.error.code", "errormsg": "$context.error.message", "requestid": "$context.requestId","apiId":"$context.apiId"}

You can add more fields to or delete existing fields from the JSON body.

.. note::

   -  The default gateway responses provided by APIG can be edited.
   -  You can create gateway responses and configure different responses for APIs in the same API group.
   -  The type of a gateway response cannot be changed. For details, see :ref:`Response Types <apig-lgug-200226001__en-us_topic_0226843033_section188951150101>`.
   -  Gateway responses can contain the API gateway context variables (starting with **$context**). For details, see :ref:`APIG Context Variables <apig-lgug-200226001__en-us_topic_0226843033_section0417113411215>`.

Prerequisites
-------------

You have created an API group.

Procedure
---------

#. Log in to the management console.
#. In the navigation pane, choose **Dedicated Gateways**. Then click **Access Console** in the upper right corner of a dedicated gateway.
#. In the navigation pane, choose **API Publishing** > **API Groups**.
#. Locate the API group for which you want to create or modify a gateway response, and click the group name to go to the API group details page.
#. Click the **Gateway Responses** tab and create a gateway response.

   .. note::

      -  To edit a response, click the **Edit** button in the upper right corner and modify the status code and content of the response.
      -  You can modify only the status code and content of a default or custom gateway response, and you cannot change the response type.
      -  Error information and other response details can be obtained using variables. For details about the supported variables, see :ref:`Table 2 <apig-lgug-200226001__en-us_topic_0226843033_table1777615351141>`.

.. _apig-lgug-200226001__en-us_topic_0226843033_section188951150101:

Response Types
--------------

:ref:`Table 1 <apig-lgug-200226001__en-us_topic_0226843033_table4964122534120>` lists the response types supported by APIG. You can define status codes of responses to meet your service requirements.

.. _apig-lgug-200226001__en-us_topic_0226843033_table4964122534120:

.. table:: **Table 1** Error Response types supported by APIG

   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Response Name                  | Default Status Code | Description                                                                                                  |
   +================================+=====================+==============================================================================================================+
   | Access Denied                  | 403                 | Access denied. For example, the access control policy is triggered or an attack is detected.                 |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Authorizer Configuration Error | 500                 | A custom authorizer error has occurred. For example, communication failed or an error response was returned. |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Authorizer Failed              | 500                 | The custom authorization failed.                                                                             |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Incorrect Identity Source      | 401                 | The identity source of the custom authorizer is missing or invalid.                                          |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Authentication Failure         | 401                 | IAM or app authentication failed.                                                                            |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Identity Source Not Found      | 401                 | No identity source has been specified.                                                                       |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Backend Timeout                | 504                 | Communication with the backend service timed out.                                                            |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Backend Unavailable            | 502                 | The backend service is unavailable due to communication error.                                               |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Default 4XX                    | ``-``               | Another 4XX error occurred.                                                                                  |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Default 5XX                    | ``-``               | Another 5XX error occurred.                                                                                  |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | No API Found                   | 404                 | No API is found.                                                                                             |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Incorrect Request Parameters   | 400                 | The request parameters are incorrect or the HTTP method is not supported.                                    |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Request Throttled              | 429                 | The request was rejected due to request throttling.                                                          |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+
   | Unauthorized App               | 401                 | The app you are using has not been authorized to call the API.                                               |
   +--------------------------------+---------------------+--------------------------------------------------------------------------------------------------------------+

.. _apig-lgug-200226001__en-us_topic_0226843033_section0417113411215:

APIG Context Variables
----------------------

.. _apig-lgug-200226001__en-us_topic_0226843033_table1777615351141:

.. table:: **Table 2** Variables that can be used in response message body

   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Variable                              | Description                                                                                                    |
   +=======================================+================================================================================================================+
   | $context.apiId                        | API ID.                                                                                                        |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.appId                        | ID of the app that calls the API.                                                                              |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.requestId                    | Request ID generated when the API is called.                                                                   |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.stage                        | Deployment environment in which the API is called.                                                             |
   +---------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | $context.sourceIp                     | Source IP address of the API caller.                                                                           |
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
