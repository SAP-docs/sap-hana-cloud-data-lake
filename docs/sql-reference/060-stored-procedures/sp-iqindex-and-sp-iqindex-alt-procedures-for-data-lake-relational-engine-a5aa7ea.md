<!-- loioa5aa7eac84f2101592f0d75aa7289f67 -->

# sp\_iqindex and sp\_iqindex\_alt Procedures for Data Lake Relational Engine

Lists information about indexes.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).





### Syntax 1

```
sp_iqindex ( [ <table_name> ],[ <column_name> ],[ <table_owner> ] )
```



### Syntax 2

```
sp_iqindex [ table_name='<tablename>' ],
[ column_name='<columnname>' ],[ table_owner='<tableowner>' ]
```



### Syntax 3

```
sp_iqindex_alt ( [ <table_name> ],[ <column_name> ],[ <table_owner> ] )
```



### Syntax 4

```
sp_iqindex_alt [ table_name='<tablename>' ],
[ column_name='<columnname>' ],[ table_owner='<tableowner>' ]
```



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Returns"/>

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

table\_name



</td>
<td valign="top">

The name of the table



</td>
</tr>
<tr>
<td valign="top">

table\_owner



</td>
<td valign="top">

The owner of the table



</td>
</tr>
<tr>
<td valign="top">

column\_name



</td>
<td valign="top">

The name of the column; multiple names can appear in a multicolumn index



</td>
</tr>
<tr>
<td valign="top">

index\_type



</td>
<td valign="top">

The abbreviated index type \(for example, `HG`\)



</td>
</tr>
<tr>
<td valign="top">

index\_name



</td>
<td valign="top">

The name of the index



</td>
</tr>
<tr>
<td valign="top">

unique\_index



</td>
<td valign="top">

'U' indicates the index is a unique index; otherwise, 'N'



</td>
</tr>
<tr>
<td valign="top">

location



</td>
<td valign="top">

TEMP = data lake Relational Engine temporary store, MAIN = data lake Relational Engine store, SYSTEM = catalog store



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



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Remarks"/>

## Remarks

Displays information about indexes in the database. Specifying one of the parameters returns the indexes from only that table, column, or tables owned by the specified user. Specifying more than one parameter filters the results by all of the parameters specified. Specifying no parameters returns all indexes for all tables in the database.

sp\_iqindex always produces one line per index. sp\_iqindex\_alt produces one line per index per column if there is a multicolumn index.



### Syntax 1

If you do not specify either of the first two parameters, but specify the next parameter in the sequence, you must substitute NULL for the omitted parameters. For example, sp\_iqindex NULL,NULL,DBA and sp\_iqindex Departments,NULL,DBA.



### Syntax 2

You can specify the parameters in any order. Enclose them in single quotes.



### Syntax 3 and 4

Produces slightly different output when a multicolumn index is present. Allows the same options as Syntax 1 and 2.



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Privileges"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Side_Effects"/>

## Side Effects

None



<a name="loioa5aa7eac84f2101592f0d75aa7289f67__IQ_Examples"/>

## Examples

-   The following variations in syntax both return all indexes on columns with the name DepartmentID:

    ```
    call sp_iqindex (NULL,'DepartmentID')
    ```

    ```
    sp_iqindex column_name='DepartmentID'
    ```


    <table>
    <tr>
    <th valign="top">

    table\_ name


    
    </th>
    <th valign="top">

    table\_ owner


    
    </th>
    <th valign="top">

    column\_ name


    
    </th>
    <th valign="top">

    index\_ type


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Departments


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentID


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Departments


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentID


    
    </td>
    <td valign="top">

    `HG`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Employees


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentID


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    </table>
    

    <table>
    <tr>
    <th valign="top">

    \(Continued\)

    index\_name


    
    </th>
    <th valign="top">

    unique\_ index


    
    </th>
    <th valign="top">

    location


    
    </th>
    <th valign="top">

    dbspace\_id


    
    </th>
    <th valign="top">

    remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T201\_C1\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T201\_C1\_HG


    
    </td>
    <td valign="top">

    U


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T202\_C5\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    </table>
    
-   The following variations in syntax both return all indexes in the table Departments that is owned by table owner GROUPO:

    ```
    sp_iqindex Departments,NULL,GROUPO
    ```

    ```
    sp_iqindex table_name='Departments',table_owner='DBA'
    ```


    <table>
    <tr>
    <th valign="top">

    table\_ name


    
    </th>
    <th valign="top">

    table\_ owner


    
    </th>
    <th valign="top">

    column\_ name


    
    </th>
    <th valign="top">

    index\_ type


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Departments


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentHeadID


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Departments


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentID


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Departments


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentID


    
    </td>
    <td valign="top">

    `HG`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Departments


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    DepartmentName


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    </table>
    

    <table>
    <tr>
    <th valign="top">

    \(Continued\)

    index\_name


    
    </th>
    <th valign="top">

    unique\_ index


    
    </th>
    <th valign="top">

    location


    
    </th>
    <th valign="top">

    dbspace\_id


    
    </th>
    <th valign="top">

    remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T201\_C3\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T201\_C1\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T201\_C1\_HG


    
    </td>
    <td valign="top">

    U


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T201\_C2\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    </table>
    
-   The following variations in syntax for sp\_iqindex\_alt both return indexes on the table Employees that contain the column City. The index emp\_loc is a multicolumn index on the columns City and State. sp\_iqindex\_alt displays one row per column for a multicolumn index:

    ```
    sp_iqindex_alt Employees,City
    ```

    ```
    sp_iqindex_alt table_name='Employees',
                   column_name='City'
    ```


    <table>
    <tr>
    <th valign="top">

    table\_ name


    
    </th>
    <th valign="top">

    table\_ owner


    
    </th>
    <th valign="top">

    column\_ name


    
    </th>
    <th valign="top">

    index\_ type


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Employees


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    City


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Employees


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    City


    
    </td>
    <td valign="top">

    `HG`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Employees


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    State


    
    </td>
    <td valign="top">

    `HG`


    
    </td>
    </tr>
    </table>
    

    <table>
    <tr>
    <th valign="top">

    \(Continued\)

    index\_name


    
    </th>
    <th valign="top">

    unique\_ index


    
    </th>
    <th valign="top">

    dbspace\_id


    
    </th>
    <th valign="top">

    remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T452\_C7\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    emp\_loc


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    emp\_loc


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    </table>
    
-   The output from sp\_iqindex for the same table and column is slightly different:

    ```
    sp_iqindex Employees,City
    ```

    ```
    sp_iqindex table_name='Employee',column_name='City'
    ```


    <table>
    <tr>
    <th valign="top">

    table\_ name


    
    </th>
    <th valign="top">

    table\_ owner


    
    </th>
    <th valign="top">

    column\_ name


    
    </th>
    <th valign="top">

    index\_ type


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Employees


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    City


    
    </td>
    <td valign="top">

    `FP`


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Employees


    
    </td>
    <td valign="top">

    GROUPO


    
    </td>
    <td valign="top">

    City,State


    
    </td>
    <td valign="top">

    `HG`


    
    </td>
    </tr>
    </table>
    

    <table>
    <tr>
    <th valign="top">

    \(Continued\)

    index\_name


    
    </th>
    <th valign="top">

    unique\_ index


    
    </th>
    <th valign="top">

    dbspace\_id


    
    </th>
    <th valign="top">

    location


    
    </th>
    <th valign="top">

    remarks


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ASIQ\_IDX\_T452\_C7\_FP


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

    \(NULL\)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    emp\_loc


    
    </td>
    <td valign="top">

    N


    
    </td>
    <td valign="top">

    16387


    
    </td>
    <td valign="top">

    Main


    
    </td>
    <td valign="top">

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

[sp\_iqpkeys Procedure for Data Lake Relational Engine](sp-iqpkeys-procedure-for-data-lake-relational-engine-a5b1c11.md "Displays information about primary keys and primary key constraints by table, column, table owner, or for all data lake Relational Engine tables in the database.")

[sp\_iqprocparm Procedure for Data Lake Relational Engine](sp-iqprocparm-procedure-for-data-lake-relational-engine-a5b2c2d.md "Displays information about stored procedure parameters, including result set variables and SQLSTATE/SQLCODE error values.")

[sp\_iq\_reset\_identity Procedure for Data Lake Relational Engine](sp-iq-reset-identity-procedure-for-data-lake-relational-engine-a5b4402.md "Sets the seed of the Identity/Autoincrement column associated with the specified table to the specified value.")

[sp\_iqtable Procedure for Data Lake Relational Engine](sp-iqtable-procedure-for-data-lake-relational-engine-a5b959d.md "Displays information about tables in the database.")

[sp\_iqview Procedure for Data Lake Relational Engine](sp-iqview-procedure-for-data-lake-relational-engine-a5bdee7.md "Displays information about views in a database.")

