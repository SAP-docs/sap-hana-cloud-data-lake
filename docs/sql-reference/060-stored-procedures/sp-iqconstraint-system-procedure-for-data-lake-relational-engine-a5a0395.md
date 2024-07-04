<!-- loioa5a0395484f210158c8090a617a7aab6 -->

# sp\_iqconstraint System Procedure for Data Lake Relational Engine

Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.



<a name="loioa5a0395484f210158c8090a617a7aab6__section_q4v_yvh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqconstraint [ '<table-name>', '<column-name>', '<table-owner>' ]
```



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1466"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

A parameter that specifies the name of the table.



</dd><dt><b>

*<column-name\>*

</b></dt>
<dd>

A parameter that specifies the name of the column.



</dd><dt><b>

*<table-owner\>*

</b></dt>
<dd>

A parameter that specifies the table owner.



</dd>
</dl>



<a name="loioa5a0395484f210158c8090a617a7aab6__section_h4t_11w_c1c"/>

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

The name of the primary enforeced table.

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

index\_name

</td>
<td valign="top">

The candidate key index.

</td>
</tr>
<tr>
<td valign="top">

CKType

</td>
<td valign="top">

The type of constraint - primary key or unique.

</td>
</tr>
<tr>
<td valign="top">

column\_name

</td>
<td valign="top">

The name of the primary key columns.

</td>
</tr>
<tr>
<td valign="top">

foreign\_table\_name

</td>
<td valign="top">

The name of the foreign table.

</td>
</tr>
<tr>
<td valign="top">

foreign\_table\_owner

</td>
<td valign="top">

The name of the foreign table owner.

</td>
</tr>
<tr>
<td valign="top">

role

</td>
<td valign="top">

The name of the foreign key role.

</td>
</tr>
<tr>
<td valign="top">

fk\_enforced

</td>
<td valign="top">

Specifies the enforced status. Valid value are: Y for enforced, N for unenforced.

</td>
</tr>
<tr>
<td valign="top">

foreign\_index\_name

</td>
<td valign="top">

The name of the foreign key index.

</td>
</tr>
<tr>
<td valign="top">

foreign\_column\_name

</td>
<td valign="top">

The name of the foreign key columns.

</td>
</tr>
<tr>
<td valign="top">

location

</td>
<td valign="top">

=The location of the constraint. Valid values are: TEMP, MAIN, or SYSTEM.

</td>
</tr>
</table>



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1468"/>

## Remarks

If table name and column name are omitted, reports all referential integrity constraints for all tables including temporary ones in the current connected database. The information includes unique or primary key constraint, referential constraint, and associated role name that are defined by the CREATE TABLE and/or ALTER TABLE statements.



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1467"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1469"/>

## Examples

This example returns all primary key/foreign key pairs where either the candidate key or foreign key contains column Col1 for owner USER1 in all tables:

```
CALL sp_iqconstraint('','Col1',USER1);
```


<table>
<tr>
<th valign="top">

table\_name

</th>
<th valign="top">

table\_owner

</th>
<th valign="top">

index\_name

</th>
<th valign="top">

CKtype

</th>
<th valign="top">

column\_

name

</th>
<th valign="top">

foreign\_

table\_

name

</th>
<th valign="top">

foreign\_

table\_

owner

</th>
<th valign="top">

role

</th>
<th valign="top">

fk\_

enforced

</th>
<th valign="top">

foreign\_

index\_name

</th>
<th valign="top">

foreign\_

column\_

name

</th>
<th valign="top">

location

</th>
</tr>
<tr>
<td valign="top">

ORDERS

</td>
<td valign="top">

USER1

</td>
<td valign="top">

ASIQ\_IDX\_T1872\_I3\_HG

</td>
<td valign="top">

PK

</td>
<td valign="top">

CUST\_ID

</td>
<td valign="top">

CUSTOMERS

</td>
<td valign="top">

USER1

</td>
<td valign="top">

ORDERS

</td>
<td valign="top">

Y

</td>
<td valign="top">

ASIQ\_IDX\_T1873\_C1\_HG

</td>
<td valign="top">

CUST\_ID

</td>
<td valign="top">

Main

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

