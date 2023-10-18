:original_name: apig-faq-190627030.html

.. _apig-faq-190627030:

App FAQs
========

**How many apps can I create?**

You can create a maximum of 50 apps.

**How do I isolate the calling information among the third parties that call the same API through app authentication?**

Create multiple apps for different third parties and bind the apps to the same API.

**Are there any restrictions on the maximum number of third parties that can call the same app through app authentication?**

No restrictions.

**Do I need to create an app for an API so that it can be called through app authentication?**

Yes, you need to create an app and bind it to the API. After the app is created, an AppKey and AppSecret are automatically created. Provide the AppKey and AppSecret for third parties to call the API.

**How can an API be called by third parties through app authentication?**

Provide third parties with the AppKey and AppSecret of the app you have created for accessing the API. The third parties then can use the AppKey and AppSecret to call the API through an SDK. For details about how to use an SDK, see **Developer Guide > Calling APIs Through App Authentication**.
