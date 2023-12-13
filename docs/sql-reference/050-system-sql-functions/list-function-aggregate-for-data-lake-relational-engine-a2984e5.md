<!-- loioa2984e5584f21015bddde2495874815d -->

# LIST Function \[Aggregate\] for Data Lake Relational Engine

Returns a delimited list of values for every row in a group.



```
LIST(
[ALL | DISTINCT] <string-expresssion>
[, <'delimiter-string'>]
[ORDER BY <order-by-expression> [ ASC | DESC ], ... ] );
```



<a name="loioa2984e5584f21015bddde2495874815d__LIST_parm1"/>

## Parameters


<dl>
<dt><b>

string-expression

</b></dt>
<dd>

A string expression, usually a column name. When ALL is specified \(the default\), for each row in the group, the value of string-expression is added to the result string, with values separated by delimiter-string. When DISTINCT is specified, only unique string-expression values are added.



</dd><dt><b>

delimiter-string

</b></dt>
<dd>

A delimiter string for the list items. The default setting is a comma. There is no delimiter if a value of NULL or an empty string is supplied. The delimiter-string must be a constant.



</dd><dt><b>

order-by-expression

</b></dt>
<dd>

Order the items returned by the function. There is no comma preceding this argument, which makes it easy to use in the case where no delimiter-string is supplied.

*<order-by-expression\>* cannot be an integer literal. However, it can be a variable that contains an integer literal.

When an ORDER BY clause contains constants, they are interpreted by the optimizer and then replaced by an equivalent ORDER BY clause. For example, the optimizer interprets ORDER BY 'a' as ORDER BY expression.

A query block containing more than one aggregate function with valid ORDER BY clauses can be executed if the ORDER BY clauses can be logically combined into a single ORDER BY clause. For example, the following clauses:

```
 ORDER BY expression1, 'a', expression2; 
```

```

 ORDER BY expression1, 'b', expression2, 'c', expression3; 
```

are subsumed by the clause:

```
 ORDER BY expression1, expression2, expression3; 
```



</dd>
</dl>



<a name="loioa2984e5584f21015bddde2495874815d__LIST_returns1"/>

## Result Set

LONG VARCHAR

> ### Note:  
> The result data type is a LONG VARCHAR. If you use LIST in a SELECT INTO statement, you must use CAST and set LIST to the correct data type and size.



<a name="loioa2984e5584f21015bddde2495874815d__LIST_remarks1"/>

## Remarks

The LIST function returns the concatenation \(with delimiters\) of all the non-NULL values of X for each row in the group. If there does not exist at least one row in the group with a definite X-value, then LIST\( X \) returns the empty string.

NULL values and empty strings are ignored by the LIST function.

A LIST function cannot be used as a window function, but it can be used as input to a window function.

This function supports NCHAR inputs and/or outputs.



<a name="loioa2984e5584f21015bddde2495874815d__LIST_standards1"/>

## Standards and Compatibility


<dl>
<dt><b>

SQL/2008

</b></dt>
<dd>

Vendor extension.

Data lake Relational Engine supports SQL/2008 language feature F441, "Extended set function support", which permits operands of aggregate functions to be arbitrary expressions that are not column references.

Data lake Relational Engine does not support optional SQL/2008 feature F442, "Mixed column references in set functions". Data lake Relational Engine does not permit the arguments of an aggregate function to include both a column reference from the query block containing the LIST function, combined with an outer reference.



</dd>
</dl>



<a name="loioa2984e5584f21015bddde2495874815d__LIST_examples1"/>

## Example

This statement returns the value ***487 Kennedy Court,547 School Street***.

```
SELECT LIST( Street ) FROM Employees
WHERE GivenName = 'Thomas'; 
```

This statement lists employee IDs. Each row in the result set contains a comma-delimited list of employee IDs for a single department.

```
SELECT LIST( EmployeeID )
FROM Employees
GROUP BY DepartmentID; 
```


<table>
<tr>
<th valign="top">

LIST\( EmployeeID \)

</th>
</tr>
<tr>
<td valign="top">

102,105,160,243,247,249,266,278,...

</td>
</tr>
<tr>
<td valign="top">

129,195,299,467,641,667,690,856,...

</td>
</tr>
<tr>
<td valign="top">

148,390,586,757,879,1293,1336,...

</td>
</tr>
<tr>
<td valign="top">

184,207,318,409,591,888,992,1062,...

</td>
</tr>
<tr>
<td valign="top">

191,703,750,868,921,1013,1570,...

</td>
</tr>
</table>

This statement sorts the employee IDs by the last name of the employee:

```
SELECT LIST( EmployeeID ORDER BY Surname ) AS "Sorted IDs"
FROM Employees
GROUP BY DepartmentID; 
```


<table>
<tr>
<th valign="top">

Sorted IDs

</th>
</tr>
<tr>
<td valign="top">

1013,191,750,921,868,1658,...

</td>
</tr>
<tr>
<td valign="top">

1751,591,1062,1191,992,888,318,...

</td>
</tr>
<tr>
<td valign="top">

1336,879,586,390,757,148,1483,...

</td>
</tr>
<tr>
<td valign="top">

1039,129,1142,195,667,1162,902,...

</td>
</tr>
<tr>
<td valign="top">

160,105,1250,247,266,249,445,...

</td>
</tr>
</table>

This statement returns semicolon-separated lists. Note the position of the ORDER BY clause and the list separator:

```
SELECT LIST( EmployeeID, ';' ORDER BY Surname ) AS "Sorted IDs"
FROM Employees
GROUP BY DepartmentID; 
```


<table>
<tr>
<th valign="top">

Sorted IDs

</th>
</tr>
<tr>
<td valign="top">

1013;191;750;921;868;1658;703;...

</td>
</tr>
<tr>
<td valign="top">

1751;591;1062;1191;992;888;318;...

</td>
</tr>
<tr>
<td valign="top">

1336;879;586;390;757;148;1483;...

</td>
</tr>
<tr>
<td valign="top">

1039;129;1142;195;667;1162;902; ...

</td>
</tr>
<tr>
<td valign="top">

160;105;1250;247;266;249;445;...

</td>
</tr>
</table>

Be sure to distinguish the previous statement from the following statement, which returns comma-separated lists of employee IDs sorted by a compound sort-key of \( Surname, ';' \):

```
SELECT LIST( EmployeeID ORDER BY Surname, ';' ) AS "Sorted IDs"
FROM Employees
GROUP BY DepartmentID; 
```

**Related Information**  


[LIST Function for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/7b4801a3a3a64799b52b9ace7257dfd9.html "Returns a delimited list of values for every row in a group.") :arrow_upper_right:

