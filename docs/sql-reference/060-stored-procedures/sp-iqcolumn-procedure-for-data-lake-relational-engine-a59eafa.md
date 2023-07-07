<!-- loioa59eafaf84f21015b9cffa01dc3a9639 -->

# sp\_iqcolumn Procedure for Data Lake Relational Engine

Displays information about columns in a database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
sp_iqcolumn ( [ <table_name> ],[ <table_owner> ], [ <table_loc> ] )
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
sp_iqcolumn [ table_name='<table_name>' ],
   [ table_owner='<tableowner>' ],[ table_loc='<table_loc>' ]
```



</dd>
</dl>



<a name="loioa59eafaf84f21015b9cffa01dc3a9639__iq_refbb_1449"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

A parameter that specifies the name of the table.



</dd><dt><b>

*<table\_owner\>*

</b></dt>
<dd>

A parameter that specifies the name of the table.



</dd><dt><b>

*<table\_loc\>*

</b></dt>
<dd>

A parameter that specifies the location of the table.



</dd>
</dl>



<a name="loioa59eafaf84f21015b9cffa01dc3a9639__section_tbj_5wz_mbb"/>

## Returns


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

table\_owner



</td>
<td valign="top">

The owner of the table.



</td>
</tr>
<tr>
<td valign="top">

column\_name



</td>
<td valign="top">

The name of the column.



</td>
</tr>
<tr>
<td valign="top">

domain\_name



</td>
<td valign="top">

The data type.



</td>
</tr>
<tr>
<td valign="top">

width



</td>
<td valign="top">

The precision of numeric data types that have precision and scale or the storage width of numeric data types without scale; the width of character data types.



</td>
</tr>
<tr>
<td valign="top">

scale



</td>
<td valign="top">

The scale of numeric data types.



</td>
</tr>
<tr>
<td valign="top">

nulls



</td>
<td valign="top">

Values are:

-   'Y' – if the column can contain NULLS
-   'N' – if the column cannot contain NULLS



</td>
</tr>
<tr>
<td valign="top">

default



</td>
<td valign="top">

'Identity/Autoincrement' if the column is an identity/autoincrement column; null if not.



</td>
</tr>
<tr>
<td valign="top">

cardinality



</td>
<td valign="top">

The distinct count, if known, by indexes.



</td>
</tr>
<tr>
<td valign="top">

location



</td>
<td valign="top">

Values are:

-   TEMP – data lake Relational Engine temporary store
-   MAIN – data lake Relational Engine main store
-   SYSTEM – catalog store



</td>
</tr>
<tr>
<td valign="top">

isPartitioned



</td>
<td valign="top">

Values are:

-   'Y' – if the column belongs to a partitioned table and has one or more partitions that have a dbspace is different from the table partition’s dbspace
-   'N' – if the column's table is not partitioned or each partition of the column resides in the same dbspace as the table partition.



</td>
</tr>
<tr>
<td valign="top">

remarks



</td>
<td valign="top">

User comments added with the `COMMENT` statement.



</td>
</tr>
<tr>
<td valign="top">

check



</td>
<td valign="top">

The check constraint expression.



</td>
</tr>
</table>



<a name="loioa59eafaf84f21015b9cffa01dc3a9639__iq_refbb_1452"/>

## Remarks

Displays information about columns in a database. Specifying the *<table\_name\>* parameter returns the columns only from tables with that name. Specifying the table\_owner parameter returns only tables owned by that user. Specifying both *<table\_name\>* and table\_owner parameters chooses the columns from a unique table, if that table exists. Specifying table\_loc returns only tables that are defined in that segment type. Specifying no parameters returns all columns for all tables in a database. sp\_iqcolumn does not return column information for system tables.



### Syntax 1

If you specify *<table\_owner\>* without specifying *<table\_name\>*, you must substitute NULL for *<table\_name\>*. For example, sp\_iqcolumn NULL,DBA.



### Syntax 2

The parameters can be specified in any order. Enclose '*<table\_name\>*' and '*<table\_owner\>*' in single quotes.



<a name="loioa59eafaf84f21015b9cffa01dc3a9639__iq_refbb_1451"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa59eafaf84f21015b9cffa01dc3a9639__section_qdm_rbf_nbb"/>

## Examples

-   The following variations in syntax both return all of the columns in the table Departments:

    ```
    sp_iqcolumn Departments
    ```

    ```
    call sp_iqcolumn (table_name='Departments')
    ```

    ```
    table_name   table_owner  column_name     domain_name  width  scale  nulls  default
    Departments  GROUPO       DepartmentID    integer       4        0   N      (NULL)
    Departments  GROUPO       DepartmentName  char         40        0   N      (NULL)
    Departments  GROUPO       DepartmentHead  integer       4        0   Y      (NULL)
    
    cardinality  location  isPartitioned  remarks  check
    5            Main       N             (NULL)   (NULL)
    0            Main       N             (NULL)   (NULL)
    0            Main       N             (NULL)   (NULL)
    ```

-   The following variation in syntax returns all of the columns in all of the tables owned by table owner DBA:

    ```
    sp_iqcolumn table_owner='DBA'
    ```


**Related Information**  


[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

