<!-- loioa5b2c2d384f21015b941b298f2b5d54c -->

# sp\_iqprocparm Procedure for Data Lake Relational Engine

Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqprocparm [ <proc-name> ], [ <proc-owner> ], [ <proc-type> ]
```



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__sp_iqprocparm_parm1"/>

## Parameters


<dl>
<dt><b>

*<proc-name\>*

</b></dt>
<dd>

\(Optional\) The name of the procedure.



</dd><dt><b>

*<proc-owner\>*

</b></dt>
<dd>

\(Optional\) The owner of the procedure.



</dd><dt><b>

*<proc-owner\>*

</b></dt>
<dd>

\(Optional\) The type of procedure. Allowed values are:

-   SYSTEM – displays information about system procedures \(procedures owned by user SYS or dbo\) only
-   ALL – displays information about user and system procedures
-   Any other value – displays information about user procedures



</dd>
</dl>



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__sp_iqprocparm_returns1"/>

## Returns


<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

proc\_name



</td>
<td valign="top">

The name of the procedure



</td>
</tr>
<tr>
<td valign="top">

proc\_owner



</td>
<td valign="top">

The owner of the procedure



</td>
</tr>
<tr>
<td valign="top">

parm\_name



</td>
<td valign="top">

The name of the parameter



</td>
</tr>
<tr>
<td valign="top">

parm\_type



</td>
<td valign="top">

The type of parameter is one of the following values:

-   Normal parameter \(variable\)
-   Result variable – used with procedures that return result sets
-   SQLSTATE error value
-   SQLCODE error value



</td>
</tr>
<tr>
<td valign="top">

parm\_mode



</td>
<td valign="top">

The mode of the parameter: whether a parameter supplies a value to the procedure, returns a value, does both, or does neither. Parameter mode is one of the following:

-   `in` – parameter supplies a value to the procedure
-   `out` – parameter returns a value
-   `inout` – parameter supplies as well as returns a value
-   NULL – parameter neither supplies nor returns a value



</td>
</tr>
<tr>
<td valign="top">

domain\_name



</td>
<td valign="top">

The name of the data type of the parameter as listed in the SYSDOMAIN system table



</td>
</tr>
<tr>
<td valign="top">

width



</td>
<td valign="top">

The length of string parameters, the precision of numeric parameters, and the number of bytes of storage for all other data types



</td>
</tr>
<tr>
<td valign="top">

scale



</td>
<td valign="top">

The number of digits after the decimal point for numeric data type parameters and zero for all other data types



</td>
</tr>
<tr>
<td valign="top">

default



</td>
<td valign="top">

The default value of the parameter, held as a string



</td>
</tr>
</table>



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__sp_iqprocparm_remarks1"/>

## Remarks

You can invoke sp\_iqprocparm without parameters. If you do not specify any parameters, input/output and result parameters of user-defined procedures \(procedures not owned by dbo or SYS\) appear.

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, sp\_iqprocparm NULL, NULL, SYSTEM and sp\_iqprocparm NULL, user1.


<table>
<tr>
<th valign="top" rowspan="1">

Syntax



</th>
<th valign="top" rowspan="1">

Output



</th>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm



</td>
<td valign="top" rowspan="1">

Displays parameters for all procedures in the database not owned by dbo or SYS.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm sp\_test



</td>
<td valign="top" rowspan="1">

Displays information about the procedure sp\_test.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm non\_existing\_proc



</td>
<td valign="top" rowspan="1">

No rows returned, as the procedure non\_existing\_proc does not exist.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm NULL, DBA



</td>
<td valign="top" rowspan="1">

Displays parameters for all procedures owned by DBA.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm sp\_test, DBA



</td>
<td valign="top" rowspan="1">

Displays parameters for the procedure sp\_test owned by DBA.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm sp\_iqtable



</td>
<td valign="top" rowspan="1">

sp\_iqtable is a system procedure. If there is no user-defined procedure also named sp\_iqtable, no rows are returned \(by default, only user-defined procedures are returned\).



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm sp\_iqtable, dbo



</td>
<td valign="top" rowspan="1">

No rows returned, as the procedure sp\_iqtable is not a user procedure \(by default, only user procedures are returned\).



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm NULL, NULL, SYSTEM



</td>
<td valign="top" rowspan="1">

Displays parameters for all system procedures \(owned by dbo or SYS\).



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm sp\_iqtable, NULL, SYSTEM



</td>
<td valign="top" rowspan="1">

Displays parameters of the system procedure sp\_iqtable.



</td>
</tr>
<tr>
<td valign="top" rowspan="1">

sp\_iqprocparm sp\_iqtable, dbo, ALL



</td>
<td valign="top" rowspan="1">

Displays parameters of the system procedure sp\_iqtable owned by dbo.



</td>
</tr>
</table>

The sp\_iqprocparm stored procedure displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values. If you specify one or more parameters, the result is filtered by the specified parameters. For example, if *<proc-name\>* is specified, only information about parameters to the specified procedure displays. If *<proc-owner\>* is specified, sp\_iqprocparm only returns information about parameters to procedures owned by the specified owner. If no parameters are specified, sp\_iqprocparm displays information about parameters to all the user-defined procedures in the database.



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__sp_iqprocparm_priv1"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__section_bt5_351_1yb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__sp_iqprocparm_sideeffects1"/>

## Side Effects

None



<a name="loioa5b2c2d384f21015b941b298f2b5d54c__sp_iqprocparm_examples1"/>

## Examples

-   Display information about the parameters of the user-defined procedure sp\_test:

    ```
    sp_iqprocparm sp_test
    ```

    ```
    proc_name proc_owner parm_name parm_type parm_mode domain_name width scale  default
    
    sp_test   DBA         ID         normal    in        integer     4     0      (NULL)
    ```

-   Display information about the parameters of the system procedure sp\_iqshowcompression:

    ```
    sp_iqprocparm sp_iqshowcompression, dbo, system
    ```

    ```
    proc_name             proc_owner  parm_name    parm_type  parm_mode  
    domain_name  width  scale  default
    
    sp_iqshowcompression  dbo         @owner_name  normal     in  
    char         128    0     (NULL)
    sp_iqshowcompression  dbo         @table_name  normal     in  
    char         128    0     (NULL)
    sp_iqshowcompression  dbo         @column_name normal     in  
    char         128    0     (NULL)
    sp_iqshowcompression  dbo         Column       result     out  
    char         128    0     (NULL)
    sp_iqshowcompression  dbo         Compression  result     out  
    char         3      0     (NULL)
    ```


**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

