:original_name: apig-faq-0009.html

.. _apig-faq-0009:

What Should I Do If the App Authentication Information Is Incorrect?
====================================================================

You may encounter the following errors related to app authentication information:

-  :ref:`Incorrect app authentication information: app not found, appkey xxx <apig-faq-0009__en-us_topic_0000001751477726_en-us_topic_0000001663636805_section1280913362208>`
-  :ref:`Incorrect app authentication information: signature expired <apig-faq-0009__en-us_topic_0000001751477726_en-us_topic_0000001663636805_section20529131916177>`

.. _apig-faq-0009__en-us_topic_0000001751477726_en-us_topic_0000001663636805_section1280913362208:

Incorrect app authentication information: app not found, appkey xxx
-------------------------------------------------------------------

.. code-block::

   {
     "error_msg": "Incorrect app authentication information: app not found, appkey 01177c425f71487ea362ba84dc4abe5e1",
     "error_code": "APIG.0303",
     "request_id": "a5322eb89048eb41d705491a76a05aca"
   }

**Possible Causes**

The AppKey is incorrect.

**Solution**

#. In the navigation pane of the APIG console, choose **API Management** > **Credentials**.
#. Click the corresponding credential name to go to the details page.
#. Check the **Key** and reconfigure the AppKey.

.. _apig-faq-0009__en-us_topic_0000001751477726_en-us_topic_0000001663636805_section20529131916177:

Incorrect app authentication information: signature expired
-----------------------------------------------------------

.. code-block::

   {
     "error_msg": "Incorrect app authentication information: signature expired, signature time:20230527T000431Z,server time:20230527T020608Z",
     "error_code": "APIG.0303",
     "request_id": "fd6530a01c09807640189e65e837b8ad"

   }

**Possible Causes**

The difference between the client's signature timestamp **x-sdk-date** and the APIG server's time exceeds 15 minutes.

**Solution**

Check whether the time on the client is correct.
