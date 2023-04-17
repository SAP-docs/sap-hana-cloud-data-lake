<!-- loioa5b3c32384f210159da494759a709b3c -->

# sp\_iqrename Procedure for Data Lake Relational Engine

Renames user-created tables, columns, indexes, constraints \(unique, primary key, foreign key, and check\), stored procedures, and functions.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqrename <object-name>, <new-name> [, <object-type> ]
```



<a name="loioa5b3c32384f210159da494759a709b3c__iq_refbb_1727"/>

## Parameters

 *<object-name\>*
 :   The original name of the user-created object.

    Optionally, *<owner-name\>* can be specified as part of *<object-name\>* as *<owner-name.object-name\>*, where *<owner-name\>* is the name of the owner of the object being renamed. If *<owner-name\>* is not specified, the user calling sp\_iqrename is assumed to be the owner of the object. The object is successfully renamed only if the user calling sp\_iqrename has the required privileges to rename the object.

    If the object to be renamed is a column, index, or constraint, you must specify the name of the table with which the object is associated. For a column, index, or constraint, *<object-name\>* can be of the form *<table-name.object-name\>* or *<owner-name.table-name.object-name\>*.

  *<new-name\>*
 :   The new name of the object. The name must conform to the rules for identifiers and must be unique for the type of object being renamed.

  *<object-type\>*
 :   \(Optional\) A parameter that specifies the type of the user-created object being renamed, that is, the type of the object *<object-name\>*. The *<object-type\>* parameter can be specified in either upper or lowercase.

    Valid values are:

    -   column – object being renamed is a column.
    -   index – object being renamed is an index.
    -   constraint – object being renamed is a unique, primary key, check, or referential \(foreign key\) constraint.
    -   procedure – object being renamed is a function.
    -   object-type not specified – object being renamed is a table.

 > ### Caution:  
> The sp\_iqrename procedure does not automatically update the definitions of dependent objects. You need to change these definitions manually.



<a name="loioa5b3c32384f210159da494759a709b3c__iq_refbb_1730"/>

## Remarks

The sp\_iqrename stored procedure renames user-created tables, columns, indexes, constraints \(unique, primary key, foreign key, and check\), and functions.

If you attempt to rename an object with a name that is not unique for that type of object, sp\_iqrename returns the message ***Item already exists***.

sp\_iqrename does not support renaming a view, a procedure, an event or a data type, and returns the message ***Feature not supported*** if you specify event or datatype as the *<object-type\>* parameter.

You can also rename using the RENAME clause of the ALTER TABLE statement and ALTER INDEX statement.



<a name="loioa5b3c32384f210159da494759a709b3c__iq_refbb_1726"/>

## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure and exclusive access to any object referenced by the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md). If you own the object referenced by the procedure, no additional privilege is required. 

For objects owned by others, additional privileges are needed, depending on the object type.


<table>
<tr>
<th valign="top">

Privilege Name



</th>
<th valign="top">

Task Allowed



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

ALTER ANY OBJECT



</td>
<td valign="top">

Rename any object.



</td>
<td valign="top" rowspan="3">

System privileges



</td>
<td valign="top" rowspan="3">

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md)



</td>
</tr>
<tr>
<td valign="top">

ALTER ANY TABLE



</td>
<td valign="top">

Rename any table, column or constraint.



</td>
</tr>
<tr>
<td valign="top">

ALTER ANY INDEX



</td>
<td valign="top">

Rename any index, but not tables or columns.



</td>
</tr>
<tr>
<td valign="top">

REFERENCES privilege on the table



</td>
<td valign="top">

Rename indexes of that table only.



</td>
<td valign="top" rowspan="2">

Object-level privileges



</td>
<td valign="top" rowspan="2">

[GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md)



</td>
</tr>
<tr>
<td valign="top">

ALTER privilege on the table



</td>
<td valign="top">

Rename that table, its columns, and constraints only.



</td>
</tr>
</table>



## Side Effects

None



<a name="loioa5b3c32384f210159da494759a709b3c__iq_refbb_1731"/>

## Examples

-   The following example renames the table titles owned by user shweta to books:

    ```
    sp_iqrename shweta.titles, books
    ```

-   The following example renames the column id of the table books to isbn:

    ```
    sp_iqrename shweta.books.id, isbn, column
    ```

-   The following example renames the index idindex on the table books to isbnindex:

    ```
    sp_iqrename books.idindex, isbnindex, index
    ```

-   The following example renames the primary key constraint prim\_id on the table books to prim\_isbn:

    ```
    sp_iqrename books.prim_id, prim_isbn, constraint
    ```


**Related Information**  


[ALTER INDEX Statement for Data Lake Relational Engine](../080-sql-statements/alter-index-statement-for-data-lake-relational-engine-a612b20.md "Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.")

[ALTER TABLE Statement for Data Lake Relational Engine](../080-sql-statements/alter-table-statement-for-data-lake-relational-engine-39f1ec0.md "Modifies a table definition.")
