:original_name: apig-api-180713009.html

.. _apig-api-180713009:

Obtaining a Project ID
======================

Calling an API
--------------

You can also obtain a project ID by calling the IAM API used to query project information.

The API used to obtain a project ID is "GET https://*{Endpoint}*/v3/projects/". *{Endpoint}* is the IAM endpoint and can be obtained from technical support. For details on API calling authentication, see :ref:`Authentication <apig-api-190529268>`.

The following is an example response. The value of **id** in the **projects** field is the project ID.

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "xx-north-4",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }

Obtaining a Project ID on the Console
-------------------------------------

A project ID needs to be specified in the URLs of some APIs. Therefore, you need to obtain a project ID before calling such APIs. To obtain a project ID, perform the following operations:

#. Log in to the management console.

#. Hover the mouse pointer over the username, click the username, and choose **My Credentials** from the drop-down list.

   On the **API Credentials** page, view project IDs in the project list.

   If there are multiple projects in one region, expand **Region** and view subproject IDs in the **Project ID** column.
