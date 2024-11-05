:original_name: apig_03_0067.html

.. _apig_03_0067:

Importing APIs
==============

You can import Swagger and OpenAPI APIs to a **new** or **existing** API group on APIG. Before importing APIs, complete the :ref:`extended definition <apig_03_0084>` of APIG.

Precautions for Importing APIs to a New Group
---------------------------------------------

When you import APIs to a new API group, the system creates an API group.

This function is suitable for importing new APIs to APIG.

Before importing APIs, ensure that the following requirements are met:

-  Your API group and API quotas are sufficient.
-  Use the **title** property in Swagger info and OpenAPI info to specify an API group name. The name of a new API group cannot be the same as that of an existing one.
-  If a conflict exists when you import APIs, the former API is imported successfully and the latter API cannot be imported. For example, if two APIs with the same name or request path exist in the imported API definition, a success message is displayed for the first imported API, and a failure message is displayed for the API to be imported subsequently.
-  If **Extended Definition Overwrite** is selected, the extended definition items (access control and request throttling policies) of an imported API will overwrite the existing extended definition items with the same name.
-  Imported APIs will not be automatically published in an environment. You can choose to publish them immediately or later.

Precautions for Importing APIs to an Existing Group
---------------------------------------------------

When you import APIs to a specified API group, the system adds them to the API group while retaining the existing APIs.

This function is suitable for importing new or modified APIs to an existing API group.

Before importing APIs, ensure that the following requirements are met:

-  Your API quota is sufficient.
-  If the definition of an API you are importing is the same as that of an existing API, you can overwrite the existing API or retain it. If you leave the existing API alone, the new API will not be imported.
-  If **Extended Definition Overwrite** is selected, the extended definition items (access control and request throttling policies) of an imported API will overwrite the existing extended definition items with the same name.
-  Imported APIs will not be automatically published in an environment. You can choose to publish them immediately or later.

Procedure
---------

#. Go to the APIG console.

#. Select a dedicated gateway at the top of the navigation pane.

#. Choose **API Management** > **APIs**.

#. Click **Import APIs**. For details, see :ref:`Importing an API Design File <apig_03_0005__en-us_topic_0000001175975942_section1427163464212>`.

   You can also import APIs to APIG by referring to the following examples:

   -  :ref:`Importing an HTTP Backend Service API <apig_03_0067__en-us_topic_0000001323925145_section199882525467>`
   -  :ref:`Importing an HTTP VPC Backend Service API <apig_03_0067__en-us_topic_0000001323925145_section28931935154811>`
   -  :ref:`Importing a Function Backend Service API <apig_03_0067__en-us_topic_0000001323925145_section8499101194913>`
   -  :ref:`Importing a Mock Backend Service API <apig_03_0067__en-us_topic_0000001323925145_section1743417117504>`

.. _apig_03_0067__en-us_topic_0000001323925145_section199882525467:

Importing an HTTP Backend Service API
-------------------------------------

Import the request parameter definition of an HTTP backend service API that uses the GET method and is accessed through IAM authentication.

Swagger example:

.. code-block::

   swagger: "2.0"
   info:
     title: "importHttpEndpoint10"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/http/{userId}':
       get:
         operationId: "getUser3"
         description: "get user by userId"
         security:
         - apig-auth-iam: []
         schemes:
         - https
         parameters:
         - name: "test"
           description: "authorization token"
           type: "string"
           in: "header"
           required: true
         - name: "userId"
           description: "user id"
           type: "string"
           in: "path"
           required: true
         responses:
           "200":
             description: "user information"
         x-apigateway-request-type: "public"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "NORMAL"
         x-apigateway-backend:
           type: "HTTP"
           parameters:
           - name: "userId"
             value: "userId"
             in: "query"
             origin: "REQUEST"
             description: "user id"
           - name: "X-Invoke-User"
             value: "apigateway"
             in: "header"
             origin: "CONSTANT"
             description: "invoke user"
           httpEndpoints:
             address: "example.com"
             scheme: "http"
             method: "GET"
             path: "/users"
             timeout: 30000
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM

OpenAPI example:

.. code-block::

   openapi: 3.0.0
   info:
     title: importHttpEndpoint10
     version: '1.0'
   servers:
     - url: >-
         http://abc.com
     - url: >-
         https://abc.com
   paths:
     '/http/{userId}':
       get:
         description: get user by userId
         operationId: getUser3
         parameters:
           - description: authorization token
             example: ''
             in: header
             name: test
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
           - description: user id
             example: ''
             in: path
             name: userId
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         security:
           - apig-auth-iam: []
         servers:
           - url: >-
               https://abc.com
         x-apigateway-backend:
           httpEndpoints:
             address: example.com
             description: ''
             enableClientSsl: false
             method: GET
             path: /users
             retryCount: '-1'
             scheme: http
             timeout: 30000
           parameters:
             - description: invoke user
               in: HEADER
               name: X-Invoke-User
               origin: CONSTANT
               value: apigateway
             - description: user id
               in: QUERY
               name: userId
               origin: REQUEST
               value: userId
           type: HTTP
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: NORMAL
         x-apigateway-request-type: public
         x-apigateway-response: default
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses:
       default: {}

.. _apig_03_0067__en-us_topic_0000001323925145_section28931935154811:

Importing an HTTP VPC Backend Service API
-----------------------------------------

Import the request parameter definition of an HTTP VPC backend service API that uses the ANY method and is accessed through app authentication.

Swagger example:

.. code-block::

   swagger: "2.0"
   info:
     title: "importHttpVpcEndpoint"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/http-vpc':
       x-apigateway-any-method:
         operationId: "userOperation"
         description: "user operation resource"
         security:
         - apig-auth-app: []
         schemes:
         - https
         parameters:
         - name: "Authorization"
           description: "authorization signature"
           type: "string"
           in: "header"
           required: true
         responses:
           "default":
             description: "endpoint response"
         x-apigateway-request-type: "public"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "SWA"
         x-apigateway-backend:
           type: "HTTP-VPC"
           parameters:
           - name: "X-Invoke-User"
             value: "apigateway"
             in: "header"
             origin: "CONSTANT"
             description: "invoke user"
           httpVpcEndpoints:
             name: "userVpc"
             scheme: "http"
             method: "GET"
             path: "/users"
             timeout: 30000
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM

OpenAPI example:

.. code-block::

   openapi: 3.0.0
   info:
     description: import apis
     title: importHttpVpcEndpoint
     version: '1.0'
   servers:
     - url: >-
         http://abc.com
     - url: >-
         https://abc.com
   paths:
     /http-vpc:
       x-apigateway-any-method:
         description: user operation resource
         operationId: userOperation
         parameters:
           - description: authorization signature
             example: ''
             in: header
             name: Authorization
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         security:
           - apig-auth-app: []
         servers:
           - url: >-
               https://abc.com
         x-apigateway-backend:
           httpVpcEndpoints:
             cascade_flag: false
             description: ''
             enableClientSsl: false
             method: GET
             name: userVpc
             path: /users
             retryCount: '-1'
             scheme: http
             timeout: 30000
           parameters:
             - description: invoke user
               in: HEADER
               name: X-Invoke-User
               origin: CONSTANT
               value: apigateway
           type: HTTP-VPC
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: SWA
         x-apigateway-request-type: public
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses: {}

.. _apig_03_0067__en-us_topic_0000001323925145_section8499101194913:

Importing a Function Backend Service API
----------------------------------------

Import the request parameter definition of a FunctionGraph backend service API that uses the GET method and is accessed through IAM authentication.

Swagger example:

.. code-block::

   swagger: "2.0"
   info:
     title: "importFunctionEndpoint"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/function/{name}':
       get:
         operationId: "invokeFunction"
         description: "invoke function by name"
         security:
         - apig-auth-iam: []
         schemes:
         - https
         parameters:
         - name: "test"
           description: "authorization token"
           type: "string"
           in: "header"
           required: true
         - name: "name"
           description: "function name"
           type: "string"
           in: "path"
           required: true
         responses:
           "200":
             description: "function result"
         x-apigateway-request-type: "public"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "NORMAL"
         x-apigateway-backend:
           type: "FUNCTION"
           parameters:
           - name: "functionName"
             value: "name"
             in: "query"
             origin: "REQUEST"
             description: "function name"
           - name: "X-Invoke-User"
             value: "apigateway"
             in: "header"
             origin: "CONSTANT"
             description: "invoke user"
           functionEndpoints:
             function-urn: "your function urn address"
             version: "your function version"
             invocation-type: "async"
             timeout: 30000
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM

OpenAPI example:

.. code-block::

   openapi: 3.0.0
   info:
     description: import apis
     title: importHttpEndpoint
     version: '1.0'
   servers:
     - url: >-
         http://api.account.com
     - url: >-
         https://api.account.com
   paths:
     /function/{name}:
       get:
         description: invoke function by name
         operationId: invokeFunction
         parameters:
           - description: function name
             in: path
             name: name
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
             example: ''
           - description: authorization token
             in: header
             name: test
             required: true
             schema:
               maxLength: 0
               maximum: 0
               minimum: 0
               type: string
             x-apigateway-pass-through: always
             example: ''
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         security:
           - apig-auth-iam: []
         servers:
           - url: >-
               https://api.account.com
         x-apigateway-backend:
           functionEndpoints:
             alias-urn: ''
             description: ''
             function-urn: "your function urn address"
             invocation-type: async
             network-type: V1
             timeout: 30000
             version: "your function version"
           parameters:
             - description: invoke user
               in: HEADER
               name: X-Invoke-User
               origin: CONSTANT
               value: apigateway
             - description: function name
               in: QUERY
               name: functionName
               origin: REQUEST
               value: name
           type: FUNCTION
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: NORMAL
         x-apigateway-request-type: public
         x-apigateway-response: default
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses:
       default: {}

.. _apig_03_0067__en-us_topic_0000001323925145_section1743417117504:

Importing a Mock Backend Service API
------------------------------------

Import the definition of a Mock backend service API that uses the GET method and is accessed without authentication.

Swagger example:

.. code-block::

   swagger: "2.0"
   info:
     title: "importMockEndpoint"
     description: "import apis"
     version: "1.0"
   host: "api.account.com"
   paths:
     '/mock':
       get:
         operationId: "mock"
         description: "mock test"
         schemes:
         - http
         responses:
           "200":
             description: "mock result"
         x-apigateway-request-type: "private"
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: "NORMAL"
         x-apigateway-backend:
           type: "MOCK"
           mockEndpoints:
             result-content: "{\"message\": \"mocked\"}"
   securityDefinitions:
     apig-auth-app:
       in: header
       name: Authorization
       type: apiKey
       x-apigateway-auth-type: AppSigv1
     apig-auth-iam:
       in: header
       name: unused
       type: apiKey
       x-apigateway-auth-type: IAM

OpenAPI example:

.. code-block::

   openapi: 3.0.0
   info:
     description: import apis
     title: importHttpVpcEndpoint
     version: '1.0'
   servers:
     - url: >-
         http://abc.com
     - url: >-
         https://abc.com
   paths:
     /mock:
       get:
         description: mock test
         operationId: mock
         responses:
           default-cors:
             description: response example
             x-apigateway-result-failure-sample: ''
             x-apigateway-result-normal-sample: ''
         servers:
           - url: >-
               http://abc.com
         x-apigateway-backend:
           mockEndpoints:
             description: ''
             result-content: '{"message": "mocked"}'
           type: MOCK
         x-apigateway-cors: true
         x-apigateway-is-send-fg-body-base64: true
         x-apigateway-match-mode: NORMAL
         x-apigateway-request-type: private
         x-apigateway-response: default
   components:
     responses:
       default-cors:
         description: response example
         headers:
           Access-Control-Allow-Origin:
             schema:
               default: '*'
               type: string
     securitySchemes:
       apig-auth-app:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-type: AppSigv1
       apig-auth-app-header:
         in: header
         name: Authorization
         type: apiKey
         x-apigateway-auth-opt:
           appcode-auth-type: header
         x-apigateway-auth-type: AppSigv1
       apig-auth-iam:
         in: header
         name: unused
         type: apiKey
         x-apigateway-auth-type: IAM
     x-apigateway-responses:
       default: {}

Follow-Up Operations
--------------------

:ref:`Publish <apig_03_0014>` the imported APIs in an environment so that they can be called by users.
