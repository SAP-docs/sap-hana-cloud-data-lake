<!-- loioa5b4402f84f21015970e99c2e7a4deaf -->

# sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine

Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iq_reset_identity ( <table_name>, <table_owner>, <value> )
```



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__iq_refbb_1734"/>

## Parameters


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

The name of the table.



</dd>
</dl>


<dl>
<dt><b>

*<table owner\>*

</b></dt>
<dd>

The name of the table owner.



</dd><dt><b>

*<value\>*

</b></dt>
<dd>

The seed value you specify to replace the default seed value.



</dd>
</dl>



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__iq_refbb_1736"/>

## Remarks

The Identity/Autoincrement column stores a number that is automatically generated. The values generated are unique identifiers for incoming data. The values are sequential, are generated automatically, and are never reused, even when rows are deleted from the table. The seed value specified replaces the default seed value and persists across database shutdowns and failures.

You need to specify *<table\_name\>*, *<table owner\>*, and *<value\>*.



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__iq_refbb_1735"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). If you own the object referenced by the procedure, no additional privilege is required. 

For objects owned by others, you need one of the following privileges:


<table>
<tr>
<th valign="top">

Privilege Name



</th>
<th valign="top">

Privilege Type



</th>
<th valign="top">

Grant Statement



</th>
</tr>
<tr>
<td valign="top">

-   ALTER ANY TABLE
-   ALTER ANY OBJECT



</td>
<td valign="top">

System privileges



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
<tr>
<td valign="top">

-   ALTER privilege on the table



</td>
<td valign="top">

Object-level privilege



</td>
<td valign="top">

[GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md)



</td>
</tr>
</table>



## Side Effects

None



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__section_nyx_y3f_nbb"/>

## Example

The following example creates an Identity column with a starting seed of 50:

```
CREATE TABLE mytable(c1 INT identity)

call sp_iq_reset_identity('mytable', 'dba', 50)
```

**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

