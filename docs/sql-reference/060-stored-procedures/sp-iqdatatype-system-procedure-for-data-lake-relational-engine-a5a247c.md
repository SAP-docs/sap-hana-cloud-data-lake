<!-- loioa5a247c884f21015aec1a5aff2384bc2 -->

# sp\_iqdatatype System Procedure for Data Lake Relational Engine

Displays information about system data types and user-defined data types.



<a name="loioa5a247c884f21015aec1a5aff2384bc2__section_tlm_jjx_4bc"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine worker as a data lake Relational Engine user.
-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user.



```
sp_iqdatatype [ <type-name>[, <type-owner>[, <type-type> ] ] ]
```



<a name="loioa5a247c884f21015aec1a5aff2384bc2__iq_refbb_1494"/>

## Parameters


<dl>
<dt><b>

*<type-name\>*

</b></dt>
<dd>

The name of the data type.



</dd><dt><b>

*<type-owner\>*

</b></dt>
<dd>

The name of the creator of the data type.



</dd><dt><b>

*<type-type\>*

</b></dt>
<dd>

The type of data type. Allowed values are:

-   SYSTEM – displays information about system defined data types \(data types owned by user SYS or dbo\) only
-   ALL – displays information about user and system data types
-   Any other value – displays information about only user data types



</dd>
</dl>



<a name="loioa5a247c884f21015aec1a5aff2384bc2__section_yyv_yrz_mbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

type\_name

</td>
<td valign="top">

The name of the data type.

</td>
</tr>
<tr>
<td valign="top">

creator

</td>
<td valign="top">

The owner of the data type.

</td>
</tr>
<tr>
<td valign="top">

nulls

</td>
<td valign="top">

Y indicates the user-defined data type allows nulls; N indicates the data type does not allow nulls and U indicates the null value for the data type is unspecified.

</td>
</tr>
<tr>
<td valign="top">

width

</td>
<td valign="top">

Displays the length of string columns, the precision of numeric columns, and the number of bytes of storage for all other data types.

</td>
</tr>
<tr>
<td valign="top">

scale

</td>
<td valign="top">

Displays the number of digits after the decimal point for numeric data type columns and zero for all other data types.

</td>
</tr>
<tr>
<td valign="top">

default

</td>
<td valign="top">

The default value for the data type.

</td>
</tr>
<tr>
<td valign="top">

check

</td>
<td valign="top">

The CHECK condition for the data type.

</td>
</tr>
</table>



<a name="loioa5a247c884f21015aec1a5aff2384bc2__section_eyx_zrz_mbb"/>

## Remarks

The sp\_iqdatatype procedure can be invoked without any parameters. If no parameters are specified, only information about user-defined data types \(data types not owned by dbo or SYS\) is displayed by default.

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, sp\_iqdatatype NULL, NULL, SYSTEM and sp\_iqdatatype NULL, user1.

The sp\_iqdatatype stored procedure displays information about system and user-defined data types in a database. User-defined data types are also referred to as domains. Predefined domain names are not included in the sp\_iqdatatype output.

If you specify one or more parameters, the sp\_iqdatatype result is filtered by the specified parameters. For example, if *<type-name\>* is specified, only information about the specified data type is displayed. If *<type-owner\>* is specified, sp\_iqdatatype only returns information about data types owned by the specified owner. If no parameters are specified, sp\_iqdatatype displays information about all the user-defined data types in the database.

The sp\_iqdatatype procedure returns information in the following columns:



<a name="loioa5a247c884f21015aec1a5aff2384bc2__iq_refbb_1493"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5a247c884f21015aec1a5aff2384bc2__iq_refbb_1499"/>

## Examples

This example returns information about the user-defined and system data types:

```
CALL sp_iqdatatype (NULL, NULL, 'ALL');
```


<table>
<tr>
<th valign="top">

type\_name

</th>
<th valign="top">

creator

</th>
<th valign="top">

nulls

</th>
<th valign="top">

width

</th>
<th valign="top">

scale

</th>
<th valign="top">

default

</th>
<th valign="top">

check

</th>
</tr>
<tr>
<td valign="top">

hs\_blockmapidentity

</td>
<td valign="top">

SYS

</td>
<td valign="top">

U

</td>
<td valign="top">

128

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

rowid

</td>
<td valign="top">

SYS

</td>
<td valign="top">

U

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

datetime

</td>
<td valign="top">

SYS

</td>
<td valign="top">

U

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

smalldatetime

</td>
<td valign="top">

SYS

</td>
<td valign="top">

U

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

text

</td>
<td valign="top">

SYS

</td>
<td valign="top">

U

</td>
<td valign="top">

32767

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

image

</td>
<td valign="top">

SYS

</td>
<td valign="top">

U

</td>
<td valign="top">

32767

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
<td valign="top">

...

</td>
</tr>
</table>

This example returns information about all user-defined data types owned by USER1:

```
CALL sp_iqdatatype (NULL, 'USER1', 'SYSTEM');
```

This example returns information about all system defined data types \(owned by dbo or SYS\):

```
CALL sp_iqdatatype (NULL, NULL, 'SYSTEM');
```

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

