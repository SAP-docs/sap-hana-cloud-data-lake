<!-- loioa5a0395484f210158c8090a617a7aab6 -->

# sp\_iqconstraint Procedure for Data Lake Relational Engine

Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



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



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1468"/>

## Remarks

If table name and column name are omitted, reports all referential integrity constraints for all tables including temporary ones in the current connected database. The information includes unique or primary key constraint, referential constraint, and associated role name that are defined by the CREATE TABLE and/or ALTER TABLE statements.



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1467"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa5a0395484f210158c8090a617a7aab6__iq_refbb_1469"/>

## Example

This is sample output that displays all primary key/foreign key pairs where either the candidate key or foreign key contains column ck1 for owner bob in all tables:

```
call sp_iqconstraint('','ck1','bob')
```

```
PTAB1 bob ASIQ_IDX_T27_HG  unique   ck1,ck2  selftab bob CK6FK3  Y  
ASIQ_IDX_T42_HG  ck1,ck2PTAB2 bob ASIQ_IDX_T27_HG  unique   ck1,ck2  selftab bob CK6FK4  Y  
ASIQ_IDX_T206_I42_HG  ck1,ck2selftab bob ASIQ_IDX_T26_HG  unique   ck1,ck2  selftab bob CK3FK1  Y  
ASIQ_IDX_T206_I42_HG  ck1,ck2
```

The columns displayed are:

-   Primary enforced table
-   Table owner
-   Candidate key index
-   Primary key or inique
-   Primary key columns
-   Foreign table
-   Foreign table owner
-   Foreign key role name
-   Enforced status \(“Y” for enforced, “N” for unenforced\)
-   Foreign key index
-   Foreign key columns
-   Location \(“TEMP,” “MAIN,” or “SYSTEM”\)

**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

