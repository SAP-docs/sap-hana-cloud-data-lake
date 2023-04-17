<!-- loioa5b1c11384f210159aebaa53583740fc -->

# sp\_iqpkeys Procedure for Data Lake Relational Engine

Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqpkeys { [ <table-name> ], [ <column-name> ], [ <table-owner> ] }
```



<a name="loioa5b1c11384f210159aebaa53583740fc__iq_refbb_1696"/>

## Parameter

 *<table-name\>*
 :   \(Optional\) The name of a base or global temporary table. If specified, the procedure returns information about primary keys defined on the specified table only.

  *<column-name\>*
 :   \(Optional\) The name of a column. If specified, the procedure returns information about primary keys on the specified column only.

  *<table-owner\>*
 :   \(Optional\) The owner of a table or table. If specified, the procedure returns information about primary keys on tables owned by the specified owner only.

 

<a name="loioa5b1c11384f210159aebaa53583740fc__section_gkl_3t4_nbb"/>

## Returns

The sp\_iqpkeys stored procedure displays the following information about primary keys on base and global temporary tables in a database:


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

The name of the column\(s\) on which the primary key is defined.



</td>
</tr>
<tr>
<td valign="top">

column\_id



</td>
<td valign="top">

The column ID.



</td>
</tr>
<tr>
<td valign="top">

constraint\_name



</td>
<td valign="top">

The name of the primary key constraint.



</td>
</tr>
<tr>
<td valign="top">

constraint\_id



</td>
<td valign="top">

The primary key constraint ID.



</td>
</tr>
</table>



<a name="loioa5b1c11384f210159aebaa53583740fc__section_fsj_ht4_nbb"/>

## Remarks

One or more of the parameters can be specified. If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. If none of the parameters are specified, a description of all primary keys on all tables in the database is displayed. If any of the specified parameters is invalid, no rows are displayed in the output.


<table>
<tr>
<th valign="top">

Syntax



</th>
<th valign="top">

Output



</th>
</tr>
<tr>
<td valign="top">

sp\_iqpkeys sales



</td>
<td valign="top">

Displays information about primary keys defined on table sales.



</td>
</tr>
<tr>
<td valign="top">

sp\_iqpkeys sales, NULL, DBA



</td>
<td valign="top">

Displays information about primary keys defined on table sales owned by DBA.



</td>
</tr>
<tr>
<td valign="top">

sp\_iqpkeys sales, store\_id, DBA



</td>
<td valign="top">

Displays information about primary key defined on column store\_id of table sales owned by DBA.



</td>
</tr>
<tr>
<td valign="top">

sp\_iqpkeys NULL, NULL, DBA



</td>
<td valign="top">

Displays information about primary keys defined on all tables owned by DBA.



</td>
</tr>
</table>



<a name="loioa5b1c11384f210159aebaa53583740fc__iq_refbb_1695"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



## Side Effects

None



<a name="loioa5b1c11384f210159aebaa53583740fc__iq_refbb_1701"/>

## Examples

-   The following example displays the primary keys defined on columns of table sales1:

    ```
    sp_iqpkeys sales1
    
    table_name table_owner column_name column_id constraint_name constraint_id
    sales1         DBA        store_id     1         MA114           114
    ```

-   The following example displays the primary keys defined on columns of table sales2:

    ```
    sp_iqpkeys sales2
    
    table_name table_owner column_name column_id constraint_name constraint_id
    sales2         DBA      store_id,     1,2        MA115           115
                            order_num
    ```

-   The following example displays the primary keys defined on the column store\_id of table sales2:

    ```
    sp_iqpkeys sales2, store_id
    
    table_name table_owner column_name column_id constraint_name constraint_id
    sales2         DBA      store_id       1         MA115           115
    ```


**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

