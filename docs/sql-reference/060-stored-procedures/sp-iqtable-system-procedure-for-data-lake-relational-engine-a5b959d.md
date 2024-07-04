<!-- loioa5b959dd84f21015a98fd3e05fb1aee9 -->

# sp\_iqtable System Procedure for Data Lake Relational Engine

Displays information about tables in the database.



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.





### Syntax 1

```
sp_iqtable ( [ <table_name> ] ,[ <table_owner> ] , [ <table_type> ] )
```

```
<table_type> ::=
    TEMP
   | VIEW
   | ALL
   | <any_other_value>
```



### Syntax 2

```
sp_iqtable [ table_name='<table_name>' ],
    [ table_owner='<table_owner>' ] , [ table_type='<table_type>' ]
```



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>* 

</b></dt>
<dd>

Specifies the name of the table.



</dd><dt><b>

*<table\_owner\>*

</b></dt>
<dd>

Specifies the table owner.



</dd><dt><b>

*<table\_type\>*

</b></dt>
<dd>

Specifies the type of table to display.

-   TEMP – Global temporary tables
-   VIEW – Views
-   ALL – data lake Relational Engine tables, global temporary tables, and views
-   *<any\_other\_value\>* – data lake Relational Engine tables



</dd>
</dl>



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__IQ_Returns"/>

## Result Set

Specifying one parameter returns only the tables that match that parameter. Specifying more than one parameter filters the results by all of the parameters specified. Specifying no parameters returns all data lake Relational Engine tables in the database. There is no method for returning the names of local temporary tables.


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

table\_name

</td>
<td valign="top">

The name of the table.

</td>
</tr>
<tr>
<td valign="top">

table\_type

</td>
<td valign="top">

The table type:

-   BASE – a base table.
-   MAT VIEW – a materialized view. \(SA tables only\)
-   GBL TEM P– a global temporary table.
-   PARTITION – a table partition \(this table is for internal use only and cannot be used by data lake Relational Engine users\).
-   VIEW – a view.



</td>
</tr>
<tr>
<td valign="top">

table\_owner

</td>
<td valign="top">

The owner of the table.

</td>
</tr>
<tr>
<td valign="top">

server\_type

</td>
<td valign="top">

The server type:

-   IQ – an object created in the data lake Relational Engine store.
-   SA – an object created in the SA store.

All views are created in the SA store.

</td>
</tr>
<tr>
<td valign="top">

location

</td>
<td valign="top">

The location:

-   TEMP – data lake Relational Engine temporary store.
-   MAIN – data lake Relational Engine store.
-   SYSTEM – catalog store.



</td>
</tr>
<tr>
<td valign="top">

dbspace\_id

</td>
<td valign="top">

Number that identifies the dbspace.

</td>
</tr>
<tr>
<td valign="top">

isPartitioned

</td>
<td valign="top">

Partition information:

-   'Y' – if the column belongs to a partitioned table and has one or more partitions whose dbspace is different from the table partition's dbspace
-   'N' – if the column's table is not partitioned or each partition of the column resides in the same dbspace as the table partition.



</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

User comments added with the COMMENT statement.

</td>
</tr>
<tr>
<td valign="top">

table\_constraints

</td>
<td valign="top">

Constraints against the table.

</td>
</tr>
<tr>
<td valign="top">

PartitionType

</td>
<td valign="top">

If partitioned, indicates the type of partition:

-   Hash-range
-   Range
-   Hash
-   None



</td>
</tr>
<tr>
<td valign="top">

isRLV

</td>
<td valign="top">

For internal use.

</td>
</tr>
</table>



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__IQ_Remarks"/>

## Remarks

For Syntax 1, if you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, `sp_iqtable NULL,NULL,TEMP` and `sp_iqtable NULL,dbo,SYSTEM`.

> ### Note:  
> The *<table\_type\>* values ALL and VIEW must be enclosed in single quotes in Syntax1.

For Syntax 2, the parameters can be specified in any order. Enclose them in single quotes.



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__IQ_Privileges"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__IQ_Side_Effects"/>

## Side Effects

None.



<a name="loioa5b959dd84f21015a98fd3e05fb1aee9__IQ_Examples"/>

## Examples

This example returns information about all tables in the database:

```
CALL sp_iqtable;
```


<table>
<tr>
<th valign="top">

Table\_

name

</th>
<th valign="top">

Table\_

type

</th>
<th valign="top">

Table\_

owner

</th>
<th valign="top">

Server\_

type

</th>
<th valign="top">

location

</th>
<th valign="top">

dbspace\_

id

</th>
<th valign="top">

is

Partitioned

</th>
<th valign="top">

Remarks

</th>
<th valign="top">

table\_

constraints

</th>
<th valign="top">

Partition

Type

</th>
<th valign="top">

is

Rlv

</th>
</tr>
<tr>
<td valign="top">

A1

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER1

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

A3

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER1

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

A4

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER1

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

D1

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER3

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

D2

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER3

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

P2

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER2

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

P4

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER2

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
</table>

This example returns all tables that are owned by USER1:

```
CALL sp_iqtable (NULL,'USER1');
```


<table>
<tr>
<th valign="top">

Table\_

name

</th>
<th valign="top">

Table\_

type

</th>
<th valign="top">

Table\_

owner

</th>
<th valign="top">

Server\_

type

</th>
<th valign="top">

location

</th>
<th valign="top">

dbspace\_

id

</th>
<th valign="top">

is

Partitioned

</th>
<th valign="top">

Remarks

</th>
<th valign="top">

table\_

constraints

</th>
<th valign="top">

Partition

Type

</th>
<th valign="top">

is

Rlv

</th>
</tr>
<tr>
<td valign="top">

P1

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER2

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

P2

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER2

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

P3

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER2

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
<tr>
<td valign="top">

P4

</td>
<td valign="top">

BASE

</td>
<td valign="top">

USER2

</td>
<td valign="top">

IQ

</td>
<td valign="top">

Main

</td>
<td valign="top">

16388

</td>
<td valign="top">

N

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

None

</td>
<td valign="top">

F

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

