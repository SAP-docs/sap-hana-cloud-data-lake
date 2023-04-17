<!-- loioa948509b70dc4210a83bb773eb91dde5 -->

# sp\_iqcheckfpconsistency Procedure for Data Lake Relational Engine

Checks consistency of default indexes created on table columns.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcheckfpconsistency ( <table_name>, <column_name>, <table_owner> )
```



<a name="loioa948509b70dc4210a83bb773eb91dde5__iq_refbb_1513"/>

## Parameters

 *<table\_name\>*
 :   The name of the table that you want to check.

  *<column\_name\>*
 :   The name of the column to check.

  *<table\_owner\>*
 :   The name of the owner of tables to check.

 

<a name="loioa948509b70dc4210a83bb773eb91dde5__iq_refbb_1561"/>

## Remarks

When you create a table, data lake Relational Engine assigns a default index to each new column. This procedure checks these indexes and diagnoses corrupted tables and columns.

All parameters are optional. You may run the procedure in several ways:

-   None – verifies all columns of all tables:

    ```
    call sp_iqcheckfpconsistency()
    ```

    > ### Note:  
    > This may take a long time.

-   Specifying only *<table\_name\>* – verifies all columns of the given table:

    ```
    call sp_iqcheckfpconsistency('<table_name>')
    ```

-   Specifying *<table\_name\>* and *<column\_name\>* – verifies *<table\_name\>*.*<column\_name\>* under all owners:

    ```
    call sp_iqcheckfpconsistency('<table_name>', '<column_name>')
    ```

-   Specifying *<table\_name\>*, *<column\_name\>*, and *<table\_owner\>* – verifies the column uniquely identified by *<table\_owner\>*.*<table\_name\>*.*<column\_name\>*

    ```
    call sp_iqcheckfpconsistency('<table_name>', '<column_name>', '<table_owner>')
    ```


The procedure returns a result table that provides a summary report. If data lake Relational Engine detects errors, it returns detailed error messages in the data lake Relational Engine message file.

Currently there is no consistency verification for columns with BIT data types. The report returns "No Errors Detected," but does not actually verify them.



## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



## Side Effects

None



## Examples

-   This statement checks consistency for all columns in the `customer` table:

    ```
    call sp_iqcheckfpconsistency('customer')  
    ```


    <table>
    <tr>
    <th valign="top">

    table\_owner


    
    </th>
    <th valign="top">

    table\_name


    
    </th>
    <th valign="top">

    column\_name


    
    </th>
    <th valign="top">

    status


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_acctbal


    
    </td>
    <td valign="top">

    Errors Detected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_address


    
    </td>
    <td valign="top">

    Errors Detected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_comment


    
    </td>
    <td valign="top">

    No Errors Detected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_custkey


    
    </td>
    <td valign="top">

    Errors Detected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_name


    
    </td>
    <td valign="top">

    Errors Detected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_phone


    
    </td>
    <td valign="top">

    Errors Detected


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ...


    
    </td>
    <td valign="top">

    ...


    
    </td>
    <td valign="top">

    ...


    
    </td>
    <td valign="top">

    ...


    
    </td>
    </tr>
    <tr>
    <td valign="top">


    
    </td>
    <td valign="top">


    
    </td>
    <td valign="top">


    
    </td>
    <td valign="top">

    See the data lake Relational Engine message file for detail error messages


    
    </td>
    </tr>
    </table>
    
-   This statement checks consistency for the column HDLADMIN.customer.c\_address:

    ```
    call sp_iqcheckfpconsistency('customer', 'c_address', 'HDLADMIN')  
    ```


    <table>
    <tr>
    <th valign="top">

    table\_owner


    
    </th>
    <th valign="top">

    table\_name


    
    </th>
    <th valign="top">

    column\_name


    
    </th>
    <th valign="top">

    status


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    HDLADMIN


    
    </td>
    <td valign="top">

    customer


    
    </td>
    <td valign="top">

    c\_address


    
    </td>
    <td valign="top">

    Errors Detected

    See the data lake Relational Engine message file for detail error messages.


    
    </td>
    </tr>
    </table>
    

