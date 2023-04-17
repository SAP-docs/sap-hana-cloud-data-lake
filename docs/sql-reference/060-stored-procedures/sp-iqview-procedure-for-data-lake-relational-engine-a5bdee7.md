<!-- loioa5bdee7a84f21015a8e0f09a5accc45a -->

# sp\_iqview Procedure for Data Lake Relational Engine

Displays information about views in a database.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



 Syntax 1
 :   ```
sp_iqview ( [ <view_name> ] , [ <view_owner> ] , [ view_type ] )
```

  Syntax 2
 :   ```
sp_iqview [ view_name='<viewname>' ],
[ view_owner='<viewowner>' ] , [ view_type='<viewtype>' ]
```

 

<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__iq_refbb_1844"/>

## Parameters

 *<view\_name\>*
 :   \(Optional\) The name of the view.

  *<view\_owner\>*
 :   \(Optional\) The owner of the view.

  `view_type`
 :   \(Optional\) The view type. Valid values are:

    -   SYSTEM – system views
    -   ALL – user and system views
    -   Any other value – user views

 

<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__section_lgk_jmm_nbb"/>

## Returns

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

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



## Side Effects

None



<a name="loioa5bdee7a84f21015a8e0f09a5accc45a__section_ur1_hcg_nbb"/>

## Examples

-   The following variations in syntax both return information about the view deptview:

    ```
    call sp_iqview('ViewSalesOrders')
    ```

    ```
    sp_iqview view_name='ViewSalesOrders'
    ```

-   The following variations in syntax both return all views that are owned by view owner GROUPO:

    ```
    sp_iqview NULL,GROUPO
    ```

    ```
    sp_iqview view_owner='GROUPO'
    ```


    <table>
    <tr>
    <th valign="top" rowspan="1">

    view\_name


    
    </th>
    <th valign="top" rowspan="1">

    view\_owner


    
    </th>
    <th valign="top" rowspan="1">

    view\_def


    
    </th>
    <th valign="top" rowspan="1">

    remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="1">

    ViewSalesOrders


    
    </td>
    <td valign="top" rowspan="1">

    GROUPO


    
    </td>
    <td valign="top" rowspan="1">

    Create views GROUPO , ViewSalesOrders\( ID, LineID, ProductID, Quantity, OrderDate, ShipDate, Region, SalesRepresentativeName


    
    </td>
    <td valign="top" rowspan="1">

    \(NULL\)


    
    </td>
    </tr>
    </table>
    

**Related Information**  


[sp\_iqcolumn Procedure for Data Lake Relational Engine](sp-iqcolumn-procedure-for-data-lake-relational-engine-a59eafa.md "Displays information about columns in a database.")

[sp\_iqconstraint Procedure for Data Lake Relational Engine](sp-iqconstraint-procedure-for-data-lake-relational-engine-a5a0395.md "Lists referential integrity constraints defined using CREATE TABLE or ALTER TABLE for the specified table or column.")

[sp\_iqdatatype Procedure for Data Lake Relational Engine](sp-iqdatatype-procedure-for-data-lake-relational-engine-a5a247c.md "Displays information about system data types and user-defined data types.")

[sp\_iqevent Procedure for Data Lake Relational Engine](sp-iqevent-procedure-for-data-lake-relational-engine-a5a872a.md "Displays information about system and user-defined events.")

[sp\_iqhelp Procedure for Data Lake Relational Engine](sp-iqhelp-procedure-for-data-lake-relational-engine-a5a978b.md "Displays information about system and user-defined objects and data types.")

[sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine](sp-iqindex-and-sp-iqindex-alt-procedures-for-data-lake-relational-engine-a5aa7ea.md "Lists information about indexes.")

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

