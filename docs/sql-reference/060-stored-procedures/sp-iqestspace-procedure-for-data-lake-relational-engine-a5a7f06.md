<!-- loioa5a7f06d84f210158e22bbecee776c23 -->

# sp\_iqestspace Procedure for Data Lake Relational Engine

Estimates the amount of space needed to create an index based on the number of rows in the table.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqestspace ( <table_name>, <#_of_rows>, <iq_page_size> )
```



<a name="loioa5a7f06d84f210158e22bbecee776c23__section_ir4_pmz_mbb"/>

## Parameters

 *<table\_name\>*
 :   A CHAR\(256\) parameter that specifies the name of the table

  *<\#\_of\_rows\>*
 :   An INT parameter that specifies the number of rows in the table

  *<iq\_page\_size\>*
 :   A SMALLINT parameter that specifies the page size defined for the data lake Relational Engine segment of the database \(must be a power of 2 between 65536 and 524288; the default is 131072\)

 

<a name="loioa5a7f06d84f210158e22bbecee776c23__iq_refbb_1561"/>

## Remarks

Displays the amount of space that a database requires based on the number of rows in the underlying database tables and on the database data lake Relational Engine page size. This procedure assumes that the database was created with the default block size for the specified data lake Relational Engine page size \(or else the estimate is incorrect\).



<a name="loioa5a7f06d84f210158e22bbecee776c23__iq_refbb_1560"/>

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

-   CREATE ANY INDEX
-   ALTER ANY INDEX
-   CREATE ANY OBJECT
-   ALTER ANY OBJECT



</td>
<td valign="top">

System privileges



</td>
<td valign="top">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
</table>



## Side Effects

None

