:original_name: apig_03_0110.html

.. _apig_03_0110:

Configuring API Parameter Orchestration Rules
=============================================

APIG supports API parameter orchestration. You can configure different algorithm rules to map new request parameters and values.

Creating an Orchestration Rule
------------------------------

#. Go to the APIG console.
#. Select a dedicated gateway at the top of the navigation pane.

3. In the navigation pane, choose **API Management** > **API Policies**.

4. Click the **Orchestration Rules** tab.

5. Click **Create Rule** and configure the parameters based on the following table.

   .. table:: **Table 1** Rule configuration

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================================================================+
      | Rule Name                         | Enter a rule name. Start with a letter and use only letters, digits, and underscores (_). 3 to 64 characters.                                                                                                                              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Orchestration Policy              | Select a policy.                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | -  **list**: Listed values are mapped to other values.                                                                                                                                                                                     |
      |                                   | -  **range**: Values in the range are mapped to other values.                                                                                                                                                                              |
      |                                   | -  **hash**: Request header values are mapped to new ones after hash calculation.                                                                                                                                                          |
      |                                   | -  **hash_range**: hash values are generated using the request parameters for range orchestration.                                                                                                                                         |
      |                                   | -  **none_value**: If the request parameter is empty, the mapping value of the **none_value** policy is returned.                                                                                                                          |
      |                                   | -  **default**: If request parameters cannot match any orchestration rule, the mapping value of the **default** policy is returned.                                                                                                        |
      |                                   | -  **head_n**: Intercept the first *n* characters of the string (If *n* is greater than the length of the string, the complete parameter value is returned.) as a temporary parameter pending orchestration for the next rule.             |
      |                                   | -  **tail_n**: Intercept the last *n* characters of the string (If *n* is greater than the length of the string, the complete parameter value is returned.) as a temporary parameter pending orchestration for the next rule.              |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Preprocessing                     | Mandatory when **Orchestration Policy** is set to **list**, **range**, **hash**, **hash_range**, **head_n**, or **tail_n**.                                                                                                                |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | Whether the rule is a preprocessing one. A preprocessing rule generates a value as a temporary parameter pending orchestration for the next rule.                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Mandatory when **Preprocessing** is disabled or **Orchestration Policy** is set to **none_value** or **default**.                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | Enter the parameter name after orchestration. Start with a letter and use only letters, digits, and hyphens (-). 1 to 128 characters.                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                              | Mandatory when **Preprocessing** is disabled or **Orchestration Policy** is set to **none_value** or **default**.                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | Select a parameter type.                                                                                                                                                                                                                   |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | -  string                                                                                                                                                                                                                                  |
      |                                   | -  number                                                                                                                                                                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Location                          | Mandatory when **Preprocessing** is disabled or **Orchestration Policy** is set to **none_value** or **default**.                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | Select a parameter location.                                                                                                                                                                                                               |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | -  header                                                                                                                                                                                                                                  |
      |                                   | -  query                                                                                                                                                                                                                                   |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Mapping                           | Mandatory when **Orchestration Policy** is set to **list**, **range**, **hash_range**, **none_value**, or **default**.                                                                                                                     |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | Enter the mapping information. Start with a letter and use only letters, digits, underscores (_), and hyphens (-). 1 to 128 characters. Use commas (,) to separate multiple parameter values. A maximum of 3,000 parameters are supported. |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | You can click **Add Mapping** to add new mappings.                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | -  **Request Parameter Value Before Orchestration**                                                                                                                                                                                        |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   |    -  When **Orchestration Policy** is set to **list**, enter the request parameter value before orchestration.                                                                                                                            |
      |                                   |    -  When **Orchestration Policy** is set to **range** or **hash_range**, enter the start value and end value of the range.                                                                                                               |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | -  **Request Parameter Value After Orchestration**: Enter the request parameter value after orchestration.                                                                                                                                 |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Length                            | Mandatory when **Orchestration Policy** is set to **head_n** or **tail_n**.                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                                            |
      |                                   | Length of the character string to be intercepted. The value ranges from 1 to 100.                                                                                                                                                          |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6. Click **OK**.

   If the created rule is displayed in the orchestration rule list, the rule is created successfully.

Related Documents
-----------------

-  After a parameter orchestration rule is created, you can associate the rule with an API. For details, see :ref:`Creating a REST API <apig_03_0010>`.
