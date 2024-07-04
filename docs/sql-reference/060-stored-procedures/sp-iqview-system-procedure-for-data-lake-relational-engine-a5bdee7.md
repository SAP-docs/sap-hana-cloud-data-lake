<!-- loioa5bdee7a84f21015a8e0f09a5accc45a -->

# sp\_iqview System Procedure for Data Lake Relational Engine

Displays information about views in a database.



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
sp_iqview ( [ <view_name> ] , [ <view_owner> ] , [ view_type ] )
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
sp_iqview [ view_name='<viewname>' ],
[ view_owner='<viewowner>' ] , [ view_type='<viewtype>' ]
```



</dd>
</dl>



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__iq_refbb_1844"/>

## Parameters


<dl>
<dt><b>

*<view\_name\>*

</b></dt>
<dd>

\(Optional\) The name of the view.



</dd><dt><b>

*<view\_owner\>*

</b></dt>
<dd>

\(Optional\) The owner of the view.



</dd><dt><b>

`view_type`

</b></dt>
<dd>

\(Optional\) The view type. Valid values are:

-   SYSTEM – system views
-   ALL – user and system views
-   Any other value – user views



</dd>
</dl>



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__section_lgk_jmm_nbb"/>

## Result Set

Specifying one of the parameters returns only the views with the specified view name or views that are owned by the specified user. Specifying more than one parameter filters the results by all of the parameters specified. Specifying no parameters returns all user views in a database.


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

view\_name

</td>
<td valign="top">

The name of the view

</td>
</tr>
<tr>
<td valign="top">

view\_owner

</td>
<td valign="top">

The owner of the view

</td>
</tr>
<tr>
<td valign="top">

view\_def

</td>
<td valign="top">

The view definition as specified in the CREATE VIEW statement

</td>
</tr>
<tr>
<td valign="top">

remarks

</td>
<td valign="top">

User comments added with the COMMENT statement

</td>
</tr>
</table>



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__iq_refbb_1845"/>

## Remarks

sp\_iqview returns a view definition greater than 32K characters without truncation.



### Syntax 1

For Syntax 1, `sp_iqview NULL,NULL,SYSTEM`, if you do not specify either of the first two parameters, but do specify the next parameter in the sequence, you must substitute NULL for the omitted parameters.

For example: `sp_iqview NULL,NULL,SYSTEM` and `sp_iqview deptview,NULL,'ALL'`.

> ### Note:  
> The *<view\_type\>* value ALL must be enclosed in single quotes in Syntax 1.



### Syntax 2

For Syntax 2, the parameters can be specified in any order, enclosed in single quotes.



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__iq_refbb_1842"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__section_ur1_hcg_nbb"/>

## Examples

This example returns information about the view V\_table:

```
call sp_iqview('V_table1');
```


<table>
<tr>
<th valign="top">

view\_name

</th>
<th valign="top">

view\_owner

</th>
<th valign="top">

view\_def

</th>
<th valign="top">

remarks

</th>
</tr>
<tr>
<td valign="top">

V\_table1

</td>
<td valign="top">

HDLADMIN

</td>
<td valign="top">

create view "HDLADMIN"."V\_table1" as select \* from "HDLADMIN"."table1"

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

This example returns all views that are owned by view owner USER2:

```
CALL sp_iqview (NULL,'USER2');
```


<table>
<tr>
<th valign="top">

view\_name

</th>
<th valign="top">

view\_owner

</th>
<th valign="top">

view\_def

</th>
<th valign="top">

remarks

</th>
</tr>
<tr>
<td valign="top">

View\_t1

</td>
<td valign="top">

USER2

</td>
<td valign="top">

create view "USER2"."View\_t1" as select \* from "SYS"."dummy"

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

View\_table1

</td>
<td valign="top">

USER2

</td>
<td valign="top">

create view "USER2"."View\_table1" as select \* from "hdladmin"."table1"

</td>
<td valign="top">

NULL

</td>
</tr>
</table>

**Related Information**  


[sp\_iqcolumn System Procedure for Data Lake Relational Engine](sp-iqcolumn-system-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint System Procedure for Data Lake Relational Engine](sp-iqconstraint-system-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype System Procedure for Data Lake Relational Engine](sp-iqdatatype-system-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent System Procedure for Data Lake Relational Engine](sp-iqevent-system-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp System Procedure for Data Lake Relational Engine](sp-iqhelp-system-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt System Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-system-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys System Procedure for Data Lake Relational Engine](sp-iqpkeys-system-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm System Procedure for Data Lake Relational Engine](sp-iqprocparm-system-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity System Procedure for Data Lake Relational Engine](sp-iq-reset-identity-system-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable System Procedure for Data Lake Relational Engine](sp-iqtable-system-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

