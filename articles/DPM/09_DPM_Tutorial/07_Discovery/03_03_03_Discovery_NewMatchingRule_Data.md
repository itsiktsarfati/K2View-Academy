### Create a New Matching Rule - Data Type

Creating a discovery rule based on the **Data** type is done by following the same steps as for the **Column** type we previously demonstrated. The difference between them is that when you select the Data **Matchcing Type** to be **Data** then the **Include pattern** and **Exclude pattern** refer to the content of the field and not to the column name. 

For example, in the Rule described below, the system will evaluate, for every field it inspects, if the content of the field meets the regular expression desccribed in the **Include Pattern** definition. 

In this case the expression describes a 9 digits number that is composed of three blocks in the length of 3, 2 and 4. As this may not apply only for SSN, you may want to attribute a lower probability to this rule compated with the rule that verified if the column name is "SOCIAL_SECURITY_NUMBER" 

![image](../images/07_Discovery_Matching_Type_Data.jpg)


[![Previous](../images/Previous.png)]( 03_03_02_Discovery_NewMatchingRule_Column.md)[<img align="right" width="60" height="54" src="../images/Next.png">](03_03_04_Discovery_NewMatchingRule_DataFunction.md)

