:original_name: en-us_topic_0084464485.html

.. _en-us_topic_0084464485:

What Are the Relationships Between an API, Environment, and App?
================================================================

An API can be published in different environments, such as RELEASE (online environment) and BETA (test environment).

An app refers to the identity of an API caller. After you create an app, the system automatically generates an AppKey and AppSecret for authenticating the app. After an API is published and assigned to an app, the owner of the app can call the API.

After publishing an API in different environments, you can define different request throttling policies and authorize different apps to call the API. For example, during the test process, API v2 is published in the BETA environment and authorized to test apps. API v1 is stable and can be authorized to all users or apps in the RELEASE environment.
