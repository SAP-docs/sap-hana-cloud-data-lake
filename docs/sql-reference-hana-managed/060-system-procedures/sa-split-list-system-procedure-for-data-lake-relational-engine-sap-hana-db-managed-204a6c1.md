<!-- loio204a6c1cac354d788d94946c8e9dbe21 -->

# sa\_split\_list System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Takes a string of values, separated by a delimiter, and returns a set of rows \(one row for each value\).



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Running Procedures](remote-execute-usage-examples-for-running-procedures-3e7f86d.md) for more information.



```
sa_split_list( 
<str>
 [, <delim>
 [, <maxlen> ] ]
)
```



<a name="loio204a6c1cac354d788d94946c8e9dbe21__section_vgd_wc2_srb"/>

## Parameters

  *<str\>* 
 :   Use this LONG VARCHAR parameter to specify the string containing the values to be split, separated by *<delim\>*.

   *<delim\>* 
 :   Use this optional CHAR\(10\) parameter to specify the delimiter used in *<str\>* to separate values. The delimiter can be a string of any characters, up to 10 bytes. If *<delim\>* is not specified, a comma is used by default.

   *<maxlen\>* 
 :   Use this optional INTEGER parameter to specify the maximum length of the returned values. For example, if *<maxlen\>* is set to 3, the values in the result set are truncated to a length of 3 characters. If you specify 0 \(the default\), values can be any length.

 

<a name="loio204a6c1cac354d788d94946c8e9dbe21__section_gwt_wc2_srb"/>

## Result Set


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



<a name="loio204a6c1cac354d788d94946c8e9dbe21__section_l4h_xc2_srb"/>

## Remarks

The sa\_split\_list procedure accepts a string with a delimited list of values, and returns a result set with one value per row. This is the opposite of the action performed by the LIST function \[Aggregate\]. An empty string is returned for row\_value if the string:

-   begins with *<delim\>* 
-   contains two successive instances of *<delim\>* in the middle of the string
-   ends with *<delim\>* 

White space within the input string is significant. If the delimiter is a space character, extra spaces in the input string result in extra rows in the result set. If the delimiter is not a space character, spaces in the input string are not trimmed from the values in the result set.



<a name="loio204a6c1cac354d788d94946c8e9dbe21__section_ivx_djx_s3b"/>

## Privileges

You have the EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio204a6c1cac354d788d94946c8e9dbe21__section_mky_xc2_srb"/>

## Side Effects

None



The following query returns a list of black colored products.

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

In the following example, the sa\_split\_list procedure is used to return the original result set from the aggregated list.

```
SELECT * 
  FROM sa_split_list( 'Tee Shirt,Baseball Cap,Visor,Shorts' );
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

The following example returns a row for each word. To avoid returning rows where row\_value is an empty string, the WHERE clause must be specified.

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

In the following example, a procedure called ProductsWithColor is created. When called, the ProductsWithColor procedure uses sa\_split\_list to parse the color values specified by the user, looks in the Color column of the Products table, and returns the name, description, size, and color for each product that matches one of the user-specified colors.

The result of the procedure call below is the name, description, size, and color of all products that are either white or black.

```
CREATE OR REPLACE PROCEDURE ProductsWithColor( IN color_list LONG VARCHAR )
BEGIN
  SELECT Name, Description, Size, Color
  FROM Products
  WHERE Color IN ( SELECT row_value FROM sa_split_list( color_list ) );
END;

SELECT * from ProductsWithColor( 'white,black' );
```

**Related Information**  


[LIST Function for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../050-system-sql-functions/list-function-for-data-lake-relational-engine-sap-hana-db-managed-7b4801a.md "Returns a delimited list of values for every row in a group.")

[sa_split_list System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/8177739d6ce21014b82ebbcba7441f0b.html "Takes a string of values, separated by a delimiter, and returns a set of rows (one row for each value).") :arrow_upper_right:

