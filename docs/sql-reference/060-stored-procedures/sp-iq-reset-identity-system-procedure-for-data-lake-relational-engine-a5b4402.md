<!-- loioa5b4402f84f21015970e99c2e7a4deaf -->

# sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine

Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__section_kbl_bbv_xyb"/>

## Result Set

None.



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__iq_refbb_1736"/>

## Remarks

The Identity/Autoincrement column stores a number that is automatically generated. The values generated are unique identifiers for incoming data. The values are sequential, are generated automatically, and are never reused, even when rows are deleted from the table. The seed value specified replaces the default seed value and persists across database shutdowns and failures.

You need to specify *<table\_name\>*, *<table owner\>*, and *<value\>*.



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__iq_refbb_1735"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.

You also need one of the following:

-   You own the object referenced by the procedure.
-   ALTER ANY TABLE system privilege
-   ALTER ANY OBJECT system privilege
-   ALTER object-level privilege on the table



## Side Effects

None.



<a name="loioa5b4402f84f21015970e99c2e7a4deaf__section_nyx_y3f_nbb"/>

## Examples

```
-- Setup for the following example ---
CREATE TABLE mytable(C1 INT IDENTITY);
```

This example resets the Identity column with a starting seed of 50:

```
CALL sp_iq_reset_identity('mytable', 'hdladmin', 50);
```

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview System Procedure for Data Lake Relational Engine](sp-iqview-system-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

