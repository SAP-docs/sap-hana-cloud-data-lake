<!-- loioa5aa7eac84f2101592f0d75aa7289f67 -->

# sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine

Lists information about indexes.



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.





### Syntax 1

```
sp_iqindex ( [ <table_name> [, <column_name> [, <table_owner> ] ] ] )
```



### Syntax 2

```
sp_iqindex [ table_name='<tablename>' ],
   [ column_name='<columnname>' [, table_owner='<tableowner>' ]
```



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__section_x1s_ynh_vzb"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the name of the indexed table.



</dd><dt><b>

*<table\_owner\>*

</b></dt>
<dd>

Specifies the owner of the indexed table.



</dd><dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the indexed column in the table.



</dd>
</dl>



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Returns"/>

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

table\_name

</td>
<td valign="top">

The name of the table

</td>
</tr>
<tr>
<td valign="top">

table\_owner

</td>
<td valign="top">

The owner of the table

</td>
</tr>
<tr>
<td valign="top">

column\_name

</td>
<td valign="top">

The name of the column; multiple names can appear in a multicolumn index

</td>
</tr>
<tr>
<td valign="top">

index\_type

</td>
<td valign="top">

The abbreviated index type \(for example, `HG`\)

</td>
</tr>
<tr>
<td valign="top">

index\_name

</td>
<td valign="top">

The name of the index

</td>
</tr>
<tr>
<td valign="top">

unique\_index

</td>
<td valign="top">

'U' indicates the index is a unique index; otherwise, 'N'

</td>
</tr>
<tr>
<td valign="top">

location

</td>
<td valign="top">

TEMP = data lake Relational Engine temporary store, MAIN = data lake Relational Engine store, SYSTEM = catalog store

</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

User comments added with the COMMENT statement

</td>
</tr>
</table>



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Remarks"/>

## Remarks

Displays information about indexes in the database. Specifying one of the parameters returns the indexes from only that table, column, or tables owned by the specified user. Specifying more than one parameter filters the results by all of the parameters specified. Specifying no parameters returns all indexes for all tables in the database.

sp\_iqindex always produces one line per index. sp\_iqindex\_alt produces one line per index per column if there is a multicolumn index.

**Syntax 1**

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, sp\_iqindex NULL,NULL,DBA and sp\_iqindex Departments,NULL,DBA.

**Syntax 2**

You can specify the parameters in any order, enclosed in single quotes.

Both syntax produces the same output.

A slightly different output is presented when a multicolumn index is present.



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Privileges"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Side_Effects"/>

## Side Effects

None.



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Examples"/>

## Examples

> ### Note:  
> The syntax variations in following examples each return the same results.

This example returns all indexes on columns with the name DepartmentID:

```
CALL sp_iqindex (NULL,'DepartmentID');
```

```
CALL sp_iqindex column_name='DepartmentID';
```


<table>
<tr>
<th valign="top">

table\_

name

</th>
<th valign="top">

table\_

owner

</th>
<th valign="top">

column\_

name

</th>
<th valign="top">

index\_

type

</th>
<th valign="top">

index\_

name

</th>
<th valign="top">

unique\_

index

</th>
<th valign="top">

location

</th>
<th valign="top">

dbspace\_

id

</th>
<th valign="top">

remarks

</th>
</tr>
<tr>
<td valign="top">

Departments

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentID

</td>
<td valign="top">

`FP`

</td>
<td valign="top">

ASIQ\_IDX\_T201\_C1\_FP

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Departments

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentID

</td>
<td valign="top">

`HG`

</td>
<td valign="top">

ASIQ\_IDX\_T201\_C1\_HG

</td>
<td valign="top">

U

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Employees

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentID

</td>
<td valign="top">

`FP`

</td>
<td valign="top">

ASIQ\_IDX\_T202\_C5\_FP

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
</table>

This example returns all indexes in the table Departments that is owned by table owner USER1:

```
CALL sp_iqindex Departments,NULL,USER1;
```

```
CALL sp_iqindex table_name='Departments',table_owner='USER1';
```


<table>
<tr>
<th valign="top">

table\_ name

</th>
<th valign="top">

table\_

owner

</th>
<th valign="top">

column\_

name

</th>
<th valign="top">

index\_

type

</th>
<th valign="top">

index\_

name

</th>
<th valign="top">

unique\_

index

</th>
<th valign="top">

location

</th>
<th valign="top">

dbspace\_

id

</th>
<th valign="top">

remarks

</th>
</tr>
<tr>
<td valign="top">

Departments

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentHeadID

</td>
<td valign="top">

`FP`

</td>
<td valign="top">

ASIQ\_IDX\_T201\_C3\_FP

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Departments

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentID

</td>
<td valign="top">

`FP`

</td>
<td valign="top">

ASIQ\_IDX\_T201\_C1\_FP

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Departments

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentID

</td>
<td valign="top">

`HG`

</td>
<td valign="top">

ASIQ\_IDX\_T201\_C1\_HG

</td>
<td valign="top">

U

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Departments

</td>
<td valign="top">

USER1

</td>
<td valign="top">

DepartmentName

</td>
<td valign="top">

`FP`

</td>
<td valign="top">

ASIQ\_IDX\_T201\_C2\_FP

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
</table>

This example returns indexes on the table Employees that contain the column City. The index emp\_loc is a multicolumn index on the columns City and State. sp\_iqindex\_alt displays one row per column for a multicolumn index:

```
CALL sp_iqindex_alt Employees,City;
```

```
CALL sp_iqindex_alt table_name='Employees', column_name='City';
```


<table>
<tr>
<th valign="top">

table\_ name

</th>
<th valign="top">

table\_

owner

</th>
<th valign="top">

column\_

name

</th>
<th valign="top">

index\_

type

</th>
<th valign="top">

index\_

name

</th>
<th valign="top">

unique\_

index

</th>
<th valign="top">

location

</th>
<th valign="top">

dbspace\_

id

</th>
<th valign="top">

remarks

</th>
</tr>
<tr>
<td valign="top">

Employees

</td>
<td valign="top">

USER1

</td>
<td valign="top">

City

</td>
<td valign="top">

`FP`

</td>
<td valign="top">

ASIQ\_IDX\_T452\_C7\_FP

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Employees

</td>
<td valign="top">

USER1

</td>
<td valign="top">

City

</td>
<td valign="top">

`HG`

</td>
<td valign="top">

emp\_loc

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
<tr>
<td valign="top">

Employees

</td>
<td valign="top">

USER1

</td>
<td valign="top">

State

</td>
<td valign="top">

`HG`

</td>
<td valign="top">

emp\_loc

</td>
<td valign="top">

N

</td>
<td valign="top">

Main

</td>
<td valign="top">

16387

</td>
<td valign="top">

\(NULL\)

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

