# sql_toolkit

## Basic

SELECT \<field names> <br>
FROM    <schema.table> 


– – comment line <br><br>
/* Long comment… <br><br>
			*/



ORDER BY	<column(s) asc/desc> – – asc is default


SELECT DISTINCT	 \<field names>


WHERE	\<filter>

<br>
<br>

## Set Operators

SELECT	\<field names><br>
FROM     	<schema.table><br>
WHERE	\<filter>

UNION                                  (also INTERSECT or EXCEPT)

SELECT	\<field names><br>
FROM     <schema.table><br>
WHERE	\<filter>

<em>
	
* UNION combines the results of both select statements. Columns must match. Duplicates are removed unless UNION ALL is used 

* INTERSECT returns only the rows that are present in both statements

* EXCEPT returns the rows in the first statement that are not present in the second statement.
</em>

<br>
<br>

## Joins

SELECT 		\<field names><br>
FROM 	 	<schema.table1><br>
INNER JOIN 	<schema.table2>              (also LEFT JOIN or RIGHT JOIN or etc.)<br>
ON 		<table1.row = table2.row><br>
WHERE 		\<filter>

<em>
	
* INNER JOIN returns only where there is a match in both tables.

* LEFT JOIN (aka LEFT OUTER JOIN) returns all rows from table1 and the matched rows from table2. null on the right side if no matches

* RIGHT JOIN (aka RIGHT OUTER JOIN) returns all rows from table2 and the matched rows from table1. null on the left side if no matches

* FULL JOIN (aka FULL OUTER JOIN) returns all rows with nulls where there is no match on either side.


<br>
<br>

## Functions

DATEDIFF(datepart, startdate, enddate) 

CAST(column AS nvarchar etc) <br>
\-- changes the data type of a column if possible.

GETDATE() <br>
\-- returns the current date and time

ISNULL(expression, replacement_value) <br>
\-- replaces null with the specified replacement

COALESCE(expression1, expression2) <br>
\-- returns the first non-null expression among the values

LEN(expression) <br>
\-- returns the length of an expression

ROUND(number, decimals) <br>
\-- rounds a number to a specified number of decimals.

TRIM(string) <br>
\-- removes leading and trailing spaces from a string

REPLACE(string, old_string, new_string) <br>

FORMAT(value, format) <br>
\-- usually used for dates and numbers

IIF(condition, true_value, false_value) <br>
\-- returns one of two values, based on whether the condition is true or false.

LEAST(expression1, expression2, expressionN) <br>
\-- Returns the lowest of the expressions. Expression can be variable or constant. EG: LEAST(base_salary, 3000) sets max salary at 3000

GREATEST(expression1, expression2, expressionN) <br>
\-- Returns the highest of the expressions. Expression can be variable or constant. EG: LEAST(base_salary, 3000) sets min salary at 3000

<br>
<br>

## Pivot

transform rows into columns

SELECT \* <br>
FROM <br><br>
( SELECT \<field names of interest> <br>
  FROM    <schema.table> ) <br><br>
PIVOT(AGG_FUNC(\<field name>))<br>
FOR(\<field to be new columns> in (list>)

Unpivot (transforms columns into rows)

SELECT * 
FROM <schema.table> <br><br>
UNPIVOT(\<new measure column> <br>
	FOR \<new column for field names> IN (list of field names))
 





