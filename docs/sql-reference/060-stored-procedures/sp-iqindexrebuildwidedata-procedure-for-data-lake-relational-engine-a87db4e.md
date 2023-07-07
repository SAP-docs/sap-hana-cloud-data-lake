<!-- loioa87db4e784f2101596f1b7355fcd2137 -->

# sp\_iqindexrebuildwidedata Procedure for Data Lake Relational Engine

Identifies wide columns in migrated databases that you need to rebuild before they are available for read/write activities.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqindexrebuildwidedata [<table.name>]
```



<a name="loioa87db4e784f2101596f1b7355fcd2137__section_hjl_dbz_mbb"/>

## Parameters


<dl>
<dt><b>

*<table.name\>*

</b></dt>
<dd>

Include the optional *<table.name\>* parameter to generate a list of wide columns for that table. Omit the *<table.name\>* parameter to generate a list of wide columns for all tables in the database.



</dd>
</dl>



<a name="loioa87db4e784f2101596f1b7355fcd2137__section_xj5_z1z_mbb"/>

## Remarks

CHAR, VARCHAR, BINARY, and VARBINARY columns wider than 255 characters, as well as all LONG VARCHAR and LONG BINARY columns in databases migrated to data lake Relational Engine 16.1 must be rebuilt before the database engine can perform read/write activities on them. sp\_iqindexrebuildwidedata identifies these columns and generates a list of statements that you can use to rebuild the columns with the sp\_iqrebuildindex procedure.



## Privileges

Requires EXECUTE object-level privilege on the procedure. If you own the object referenced by the procedure, no additional privilege is required.

For objects owned by others, you need one of the following privileges:

-   INSERT ANY TABLE system privilege
-   INSERT object-level privilege on the table



## Side Effects

None



## Example

This example generates wide-column rebuild statements for table T2:

```
sp_iqindexrebuildwidedata T2
```

```

Owner  Table  Column  Domain    Width    IndexType            sp_iqrebuild
DBA    T2     C1      char      1020     Long varchar FP      sp_iqrebuildindex '"DBA.T2"'  'column "C1"  0';  
```

