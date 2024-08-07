<!-- loio268f1ef2cade4d43be01e422595d548a -->

# sa\_describe\_query System Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Describes the result set for a query with one row describing each output column of the query.



<a name="loio268f1ef2cade4d43be01e422595d548a__section_gz5_gcf_pzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE\_QUERY.
-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_describe_query( <query>[, <add_keys> ] )
```



## Parameters


<dl>
<dt><b>

*<query\>* 

</b></dt>
<dd>

Use this LONG VARCHAR parameter to specify the text of the SQL statement being described.



</dd><dt><b>

*<add\_keys\>* 

</b></dt>
<dd>

Use this optional BIT parameter to specify whether to determine a set of columns that uniquely identify rows in the result set for the query being described. The default is 0; the database server does not attempt to identify the columns. See the Remarks section below for a full explanation of this parameter.



</dd>
</dl>



<a name="loio268f1ef2cade4d43be01e422595d548a__section_z3q_d2x_tvb"/>

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

column\_number

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The ordinal position of the column described by this row, starting at 1.

</td>
</tr>
<tr>
<td valign="top">

name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the column.

</td>
</tr>
<tr>
<td valign="top">

domain\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The data type of the column.

</td>
</tr>
<tr>
<td valign="top">

domain\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The data type name.

</td>
</tr>
<tr>
<td valign="top">

domain\_name\_with\_size

</td>
<td valign="top">

VARCHAR\(160\)

</td>
<td valign="top">

The data type name, including size and precision \(as used in CREATE TABLE or CAST functions\).

</td>
</tr>
<tr>
<td valign="top">

width

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The length of a string parameter, the precision of a numeric parameter, or the number of bytes of storage for any other data type.

</td>
</tr>
<tr>
<td valign="top">

scale

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The number of digits after the decimal point for numeric data type columns, and zero for all other data types.

</td>
</tr>
<tr>
<td valign="top">

declared\_width

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

The length of a string parameter, the precision of a numeric parameter, or the number of bytes of storage for any other data type.

</td>
</tr>
<tr>
<td valign="top">

user\_type\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

The type\_id of the user-defined data type if there is one, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

user\_type\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The name of the user-defined data type if there is one, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

correlation\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The correlation name associated with the expression if one is available, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

base\_table\_id

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The table\_id if the expression is a column, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

base\_column\_id

</td>
<td valign="top">

UNSIGNED INTEGER

</td>
<td valign="top">

The column\_id if the expression is a column, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

base\_owner\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The owner name if the expression is a column, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

base\_table\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The table name if the expression is a column, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

base\_column\_name

</td>
<td valign="top">

VARCHAR\(128\)

</td>
<td valign="top">

The column name if the expression is a column, otherwise NULL.

</td>
</tr>
<tr>
<td valign="top">

nulls\_allowed

</td>
<td valign="top">

BIT

</td>
<td valign="top">

An indicator that is 1 if the expression can be NULL, otherwise 0.

</td>
</tr>
<tr>
<td valign="top">

is\_autoincrement

</td>
<td valign="top">

BIT

</td>
<td valign="top">

An indicator that is 1 if the expression is a column declared to be AUTOINCREMENT, otherwise 0.

</td>
</tr>
<tr>
<td valign="top">

is\_key\_column

</td>
<td valign="top">

BIT

</td>
<td valign="top">

An indicator that is 1 if the expression is part of a key for the result set, otherwise 0. For more information, see the Remarks section below.

</td>
</tr>
<tr>
<td valign="top">

is\_added\_key\_column

</td>
<td valign="top">

BIT

</td>
<td valign="top">

An indicator that is 1 if the expression is an added key column, otherwise 0. For more information, see the Remarks section below.

</td>
</tr>
</table>



<a name="loio268f1ef2cade4d43be01e422595d548a__section_pg1_h2x_tvb"/>

## Remarks

The sa\_describe\_query procedure provides an API-independent mechanism to describe the name and type information for the expressions in the result set of a query.

When 1 is specified for *<add\_keys\>*, the sa\_describe\_query procedure attempts to find a set of columns from the objects being queried that, when combined, can be used as a key to uniquely identify rows in result set of the query being described. The key takes the form of one or more columns from the objects being queried, and may include columns that are not explicitly referenced in the query. If the optimizer finds a key, the column or columns used in the key are identified in the results by an is\_key\_column value of 1. If no key is found, an error is returned.

For any column that is included in the key but that is not explicitly referenced in the query, the is\_added\_key\_column value is set to 1 to indicate that the column has been added to the results for the procedure; otherwise, the value of is\_added\_key\_column is 0.

If you do not specify *<add\_keys\>*, or you specify a value of 0, the optimizer does not attempt to find a key for the result set, and the is\_key\_column and is\_added\_key\_column columns contain NULL.

The declared\_width and width values both describe the size of a column. The declared\_width describes the size of the column as defined by the CREATE TABLE statement or by the query, while the width value depends on the data type.

The client representation of a type may be different from the database server. For example, DATE, TIME, and TIMESTAMP data types are converted to strings if the return\_date\_time\_as\_string option is on. The TIMESTAMP WITH TIME ZONE data type is always formatted as a string when sent to the client. The width value for these types is based solely on the length of corresponding format option string and may or may not reflect that actual formatted length. For example, specifying more than 6 digits of precision for the fractional seconds part will affect the width value, but the actual formatted string will have at most 6 digits of precision.

For CHARACTER data types, columns declared with character-length semantics have a declared\_width value that matches the CREATE TABLE size, while the width value gives the maximum number of bytes needed to store the returned string.

For NUMERIC, DECIMAL, FLOAT, REAL, and DOUBLE data types, declared\_width and width are identical. The width does not represent the length of the formatted string which may include sign and decimal point indicators. For numeric/decimal values, width represents the precision. For floating-point values, width represents the storage size in bytes.

The following table provides some examples.


<table>
<tr>
<th valign="top">

Declaration

</th>
<th valign="top">

width

</th>
<th valign="top">

declared\_width

</th>
</tr>
<tr>
<td valign="top">

CHAR\(10\)

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

CHAR\(10 CHAR\)

</td>
<td valign="top">

40

</td>
<td valign="top">

10

</td>
</tr>
<tr>
<td valign="top">

DATE

</td>
<td valign="top">

depends on the length of the date\_format option string

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

DOUBLE

</td>
<td valign="top">

8

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

REAL

</td>
<td valign="top">

4

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

NUMERIC\(10, 3\)

</td>
<td valign="top">

10 \(precision\)

</td>
<td valign="top">

10 \(precision\)

</td>
</tr>
<tr>
<td valign="top">

TIME

</td>
<td valign="top">

depends on the length of the time\_format option string

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

depends on the length of the timestamp\_format option string

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

depends on the length of the timestamp\_with\_time\_zone\_format option string

</td>
<td valign="top">

8

</td>
</tr>
</table>



<a name="loio268f1ef2cade4d43be01e422595d548a__section_uv1_d1b_1yb"/>

## Privileges



### 

The privileges required depend on your data lake Relational Engine \(SAP HANA DB-Managed\) connection method:


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user and using REMOTE\_EXECUTE\_QUERY:

</b></dt>
<dd>

Requires the REMOTE EXECUTE privilege on the remote source *<hana\_relational\_container\_schema\>*\_SOURCE.

-   See [REMOTE\_EXECUTE\_QUERY Guidance and Examples for Running Stored Procedures](remote-execute-query-guidance-and-examples-for-running-stored-procedures-3e7f86d.md).




</dd><dt><b>

Connected directly to data lake Relational Engine as a data lake Relational Engine user:

</b></dt>
<dd>

Requires EXECUTE object-level privilege on this procedure. Also requires one of the following:

-   You own the underlying table of the query
-   SELECT object-level privilege on the table



</dd>
</dl>



<a name="loio268f1ef2cade4d43be01e422595d548a__section_d3d_s2x_tvb"/>

## Side Effects

None.



## Examples

This example returns the result set when querying all columns in the table dummy:

```
CALL sa_describe_query( 'SELECT * FROM dummy' );
```

The results show the values of the is\_key\_column and is\_added\_key\_column as NULL because the *<add\_keys\>* parameter was not specified.


<table>
<tr>
<th valign="top">

column\_

number

</th>
<th valign="top">

name

</th>
<th valign="top">

domain\_

id

</th>
<th valign="top">

domain\_

name

</th>
<th valign="top">

domain\_

name\_

with\_

size

</th>
<th valign="top">

width

</th>
<th valign="top">

scale

</th>
<th valign="top">

declared\_

width

</th>
<th valign="top">

user\_

type\_

id

</th>
<th valign="top">

user\_

type\_

name

</th>
<th valign="top">

correlation\_

name

</th>
<th valign="top">

...

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

dummy\_col

</td>
<td valign="top">

2

</td>
<td valign="top">

integer

</td>
<td valign="top">

integer

</td>
<td valign="top">

4

</td>
<td valign="top">

0

</td>
<td valign="top">

4

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

DUMMY

</td>
<td valign="top">

...

</td>
</tr>
</table>

**Related Information**  


[sa_describe_query System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/8174bd7b6ce21014b1c9f89d8beb41cb.html "Describes the result set for a query with one row describing each output column of the query.") :arrow_upper_right:

