# Creating an LUDB Function

### What Is an LUDB Function?

An LUDB function is a Project function invoked from an SQL query to perform more complex operations on LU (it is a must to run get/use to see the LUDB functions) or reference data (always available) than those performed using standard SQL statements.
*	LUDB functions are invoked from an SQL statement.
*	LUDB functions must have at least one Output value.

### How Do I Create or Edit an LUDB Function? 
To create an LUDB function, refer to the steps in [How to Create Project Functions](/articles/07_table_population/10_creating_a_project_function.md).

![image](images/07_09_01_screen1.png)

When creating an LUBD function, make sure that:
*	**Function Type = LUDB Function.** 
*	The LUDB function returns at least one Output parameter.

### Example of an LUDB Function

1.	Create a new function with **Function Type = LUDB Function**.
2.	Define the Input (optional) and **Output** parameters of the function.
3.	Create another function, for example a **Root function**, that invokes the **LUDB function** from the **SELECT** statement:

~~~java
String sql = 
"SELECT CUSTOMER_ID, ACTIVITY_ID, ACTIVITY_DATE, ACTIVITY_NOTE, fnCreateInstId(?) IID FROM Customer.ACTIVITY";
Db.Rows rows = ludb().fetch(sql,input);
for (Db.Row row:rows){
	yield(row.cells());
}
~~~

Full example of **fnCreateInstId** LUDB Function can be found in the Demo project.

[![Previous](/articles/images/Previous.png)](/articles/07_table_population/11_2_root_functions_code_examples.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](/articles/07_table_population/11_4_creating_a_trigger_function.md)
