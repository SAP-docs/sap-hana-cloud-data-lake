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

 *<table.name\>*
 :   Include the optional *<table.name\>* parameter to generate a list of wide columns for that table. Omit the *<table.name\>* parameter to generate a list of wide columns for all tables in the database.

 

<a name="loioa87db4e784f2101596f1b7355fcd2137__section_xj5_z1z_mbb"/>

## Remarks

CHAR, VARCHAR, BINARY, and VARBINARY columns wider than 255 characters, as well as all LONG VARCHAR and LONG BINARY columns in databases migrated to data lake Relational Engine 16.1 must be rebuilt before the database engine can perform read/write activities on them. sp\_iqindexrebuildwidedata identifies these columns and generates a list of statements that you can use to rebuild the columns with the sp\_iqrebuildindex procedure.



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

INSERT ANY TABLE



</td>
<td valign="top">

System privilege



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
<tr>
<td valign="top">

INSERT privilege on the table



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



## Example

This example generates wide-column rebuild statements for table T2:

```
sp_iqindexrebuildwidedata T2
```

```

Owner  Table  Column  Domain    Width    IndexType            sp_iqrebuild
DBA    T2     C1      char      1020     Long varchar FP      sp_iqrebuildindex '"DBA.T2"'  'column "C1"  0';  
```

