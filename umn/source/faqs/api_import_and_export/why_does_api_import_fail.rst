:original_name: apig-faq-2005024.html

.. _apig-faq-2005024:

Why Does API Import Fail?
=========================

Possible cause 1: The number of APIs exceeds the maximum allowed limit for a single import. For more APIs (300), import them in batches or submit a service ticket to increase the limit.

Possible cause 2: Parameters are incorrect. Check and rectify the parameters. You are advised to create an API on the APIG console, export it, and then use it as a template for importing APIs.

Possible cause 3: The YAML file is in incorrect format. Check and modify the file.

Possible cause 4: The local proxy network has restrictions. Change the network environment.

Possible cause 5: The header of the API request contains **X-Auth-Token**. Remove **X-Auth-Token** from the header.
