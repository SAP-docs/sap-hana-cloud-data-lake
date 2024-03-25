<!-- loio8177739d6ce21014b82ebbcba7441f0b -->

# sa\_split\_list System Procedure for Data Lake Relational Engine

Takes a string of values, separated by a delimiter, and returns a set of rows \(one row for each value\).



<a name="loio8177739d6ce21014b82ebbcba7441f0b__section_p4t_vqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_split_list( <str>[, <delim>
   [, <maxlen> ] ] )
```



<a name="loio8177739d6ce21014b82ebbcba7441f0b__sa_split_list_parm1"/>

## Parameters


<dl>
<dt><b>

*<str\>* 

</b></dt>
<dd>

Use this LONG VARCHAR parameter to specify the string containing the values to be split, separated by *<delim\>*.



</dd><dt><b>

*<delim\>* 

</b></dt>
<dd>

Use this optional CHAR\(10\) parameter to specify the delimiter used in *<str\>* to separate values. The delimiter can be a string of any characters, up to 10 bytes. If *<delim\>* is not specified, a comma is used by default.



</dd><dt><b>

*<maxlen\>* 

</b></dt>
<dd>

Use this optional INTEGER parameter to specify the maximum length of the returned values. For example, if *<maxlen\>* is set to 3, the values in the result set are truncated to a length of 3 characters. If you specify 0 \(the default\), values can be any length.



</dd>
</dl>



<a name="loio8177739d6ce21014b82ebbcba7441f0b__sa_split_list_resultset1"/>

## Results Set


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*line\_num*

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Sequential number for the row.

</td>
</tr>
<tr>
<td valign="top">

*row\_value*

</td>
<td valign="top">

LONG VARCHAR

</td>
<td valign="top">

Value from the string, truncated to *<maxlen\>* if required.

</td>
</tr>
</table>



<a name="loio8177739d6ce21014b82ebbcba7441f0b__sa_split_list_remarks1"/>

## Remarks

The sa\_split\_list procedure accepts a string with a delimited list of values, and returns a result set with one value per row. This is the opposite of the action performed by the LIST function \[Aggregate\]. An empty string is returned for row\_value if the string:

-   begins with *<delim\>* 
-   contains two successive instances of *<delim\>* in the middle of the string
-   ends with *<delim\>* 

White space within the input string is significant. If the delimiter is a space character, extra spaces in the input string result in extra rows in the result set. If the delimiter is not a space character, spaces in the input string are not trimmed from the values in the result set.



<a name="loio8177739d6ce21014b82ebbcba7441f0b__sa_split_list_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loio8177739d6ce21014b82ebbcba7441f0b__sa_split_list_sideeffects1"/>

## Side Effects

None



<a name="loio8177739d6ce21014b82ebbcba7441f0b__sa_split_list_examples1"/>

## Examples

```
-- Setup for the following examples ---
CREATE TABLE PRODUCTS (NAME VARCHAR(15), COLOR VARCHAR(10));
INSERT INTO PRODUCTS  VALUES ('Tee Shirt','Black');
INSERT INTO PRODUCTS VALUES ('Baseball Cap', 'Black');
INSERT INTO PRODUCTS VALUES ('Visor', 'Black');
INSERT INTO PRODUCTS VALUES ('Shorts', 'Black');;
```

This example returns a list of black colored products.

```
SELECT list( Name )
  FROM Products 
  WHERE Color = 'Black';
```


<table>
<tr>
<th valign="top">

list \(Products.Name\)

</th>
</tr>
<tr>
<td valign="top">

Tee Shirt,Baseball Cap,Visor,Shorts

</td>
</tr>
</table>

This example uses the sa\_split\_list system procedure to return the original result set from the aggregated list.

```
CALL sa_split_list( 'Tee Shirt,Baseball Cap,Visor,Shorts' );
```


<table>
<tr>
<th valign="top">

line\_num

</th>
<th valign="top">

row\_value

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

Tee Shirt

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

Baseball Cap

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

Visor

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

Shorts

</td>
</tr>
</table>

This example returns a row for each word. To avoid returning rows where row\_value is an empty string, the WHERE clause must be specified.

```
SELECT *
  FROM sa_split_list( 'one||three|four||six|', '|' ) 
  WHERE row_value <> '';
```


<table>
<tr>
<th valign="top">

line\_num

</th>
<th valign="top">

row\_value

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

one

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

three

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

four

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

six

</td>
</tr>
</table>

**Related Information**  


[LIST Function \[Aggregate\] for Data Lake Relational Engine](../050-system-sql-functions/list-function-aggregate-for-data-lake-relational-engine-a2984e5.md "Returns a delimited list of values for every row in a group.")

[sa_split_list System Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/204a6c1cac354d788d94946c8e9dbe21.html "Takes a string of values, separated by a delimiter, and returns a set of rows (one row for each value).") :arrow_upper_right:

