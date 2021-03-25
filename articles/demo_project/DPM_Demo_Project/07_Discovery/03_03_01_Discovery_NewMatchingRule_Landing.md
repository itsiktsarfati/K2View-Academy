## Create a New Matching Rule

When you create a New Matching Rule for the Discovery process, you need to specify a Matching Type. Your selection determines additional fields that display during the creation process, allowing you to further narrow the scope of the rule. There are four Matching Types: Column, Data, Data Function, and Data Sample.

### Column Matching Type <hyperlink to article>

The Column Matching Type lets you configure rules that inspect the column names in the databases that are scanned, and then compare them with an expression you define in the Match Pattern field. Using this option, you can see if the column contains PII data.

### Data Matching Type<hyperlink to article>

The Data Matching Type lets you narrow your view to the data inside a column. This rule compares data in the database within a column using a set of predefined values.

### Data Function Matching Type<hyperlink to article>

The Data Function Matching Type lets you run a function on the content of a sample population from a table. The function verifies the content of the table or column is a valid format. You can set the Probability (percentage) that the function will return content that is PII data.

### Data Sample Matching Type<hyperlink to article>

The Data Sample Matching Type lets you compare the column content with what a customer provided. You only need to load the function into the table.

