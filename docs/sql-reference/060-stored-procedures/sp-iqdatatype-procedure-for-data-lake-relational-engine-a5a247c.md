<!-- loioa5a247c884f21015aec1a5aff2384bc2 -->

# sp\_iqdatatype Procedure for Data Lake Relational Engine

Displays information about system data types and user-defined data types.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqdatatype [ <type-name> ], [ <type-owner> ], [ <type-type> ]
```



<a name="loioa5a247c884f21015aec1a5aff2384bc2__iq_refbb_1494"/>

## Parameters


<dl>
<dt><b>

*<type-name\>*

</b></dt>
<dd>

The name of the data type.



</dd><dt><b>

*<type-owner\>*

</b></dt>
<dd>

The name of the creator of the data type.



</dd><dt><b>

*<type-type\>*

</b></dt>
<dd>

The type of data type. Allowed values are:

-   SYSTEM – displays information about system defined data types \(data types owned by user SYS or dbo\) only
-   ALL – displays information about user and system data types
-   Any other value – displays information about user data types



</dd>
</dl>



<a name="loioa5a247c884f21015aec1a5aff2384bc2__section_yyv_yrz_mbb"/>

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

type\_name



</td>
<td valign="top">

The name of the data type.



</td>
</tr>
<tr>
<td valign="top">

creator



</td>
<td valign="top">

The owner of the data type.



</td>
</tr>
<tr>
<td valign="top">

nulls



</td>
<td valign="top">

Y indicates the user-defined data type allows nulls; N indicates the data type does not allow nulls and U indicates the null value for the data type is unspecified.



</td>
</tr>
<tr>
<td valign="top">

width



</td>
<td valign="top">

Displays the length of string columns, the precision of numeric columns, and the number of bytes of storage for all other data types.



</td>
</tr>
<tr>
<td valign="top">

scale



</td>
<td valign="top">

Displays the number of digits after the decimal point for numeric data type columns and zero for all other data types.



</td>
</tr>
<tr>
<td valign="top">

"default"



</td>
<td valign="top">

The default value for the data type.



</td>
</tr>
<tr>
<td valign="top">

"check"



</td>
<td valign="top">

The CHECK condition for the data type.



</td>
</tr>
</table>



<a name="loioa5a247c884f21015aec1a5aff2384bc2__section_eyx_zrz_mbb"/>

## Remarks

The sp\_iqdatatype procedure can be invoked without any parameters. If no parameters are specified, only information about user-defined data types \(data types not owned by dbo or SYS\) is displayed by default.

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, sp\_iqdatatype NULL, NULL, SYSTEM and sp\_iqdatatype NULL, user1.

The sp\_iqdatatype stored procedure displays information about system and user-defined data types in a database. User-defined data types are also referred to as domains. Predefined domain names are not included in the sp\_iqdatatype output.

If you specify one or more parameters, the sp\_iqdatatype result is filtered by the specified parameters. For example, if *<type-name\>* is specified, only information about the specified data type is displayed. If *<type-owner\>* is specified, sp\_iqdatatype only returns information about data types owned by the specified owner. If no parameters are specified, sp\_iqdatatype displays information about all the user-defined data types in the database.

The sp\_iqdatatype procedure returns information in the following columns:



<a name="loioa5a247c884f21015aec1a5aff2384bc2__iq_refbb_1493"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None



<a name="loioa5a247c884f21015aec1a5aff2384bc2__iq_refbb_1499"/>

## Examples

-   The following example displays information about the user-defined data type country\_t:

    ```
    sp_iqdatatype country_t
    
    type_name    creator    nulls    width    scale    "default"    "check"
    country_t    DBA        U       15        0         (NULL)       (NULL)
    ```

-   The following example displays information about all user-defined data types in the database:

    ```
    sp_iqdatatype
    ```

-   The following example displays information about the user-defined data type named country\_t:

    ```
    sp_iqdatatype country_t
    ```

-   In the following example, no rows are returned, as the data type non\_existing\_type does not exist:

    ```
    sp_iqdatatype non_existing_type
    ```

-   The following example displays information about all user-defined data types owned by DBA:

    ```
    sp_iqdatatype NULL, DBA
    ```

-   The following example displays information about the data type country\_t owned by DBA:

    ```
    sp_iqdatatype country_t, DBA
    ```

-   In the following example, rowid is a system-defined data type. If there is no user-defined data type also named rowid, no rows are returned. \(By default, only user-defined data types are returned.\):

    ```
    sp_iqdatatype rowid
    ```

-   In the following example, no rows are returned, as the data type `rowid` is not a user-defined data type \(by default, only user-defined data types are returned\):

    ```
    sp_iqdatatype rowid, SYS
    ```

-   The following example displays information about all system defined data types \(owned by dbo or SYS\):

    ```
    sp_iqdatatype NULL, NULL, SYSTEM
    ```

-   The following example displays information about the system data type rowid:

    ```
    sp_iqdatatype rowid, NULL, SYSTEM
    ```

-   The following example displays information about the user-defined and system data types:

    ```
    sp_iqdatatype NULL, NULL, 'ALL'
    ```


**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

