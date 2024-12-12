:original_name: apig_0084464485.html

.. _apig_0084464485:

What Are the Relationships Between an API, Environment, and App (Credential)?
=============================================================================

An API can be published in different environments, such as RELEASE (online environment) and BETA (test environment).

An app (credential) refers to the identity of an API caller. After you create an app (credential), the system automatically generates a key and secret for authenticating the app (credential). After an API is published and assigned to an app (credential), the owner of the app (credential) can call the API.

After publishing an API in different environments, you can define different request throttling policies and authorize different apps (credentials) to call the API. For example, during the test process, API v2 is published in the BETA environment and authorized to test apps (credentials). API v1 is stable and can be authorized to all users or apps (credentials) in the RELEASE environment.
