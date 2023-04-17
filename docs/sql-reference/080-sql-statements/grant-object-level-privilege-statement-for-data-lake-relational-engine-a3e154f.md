<!-- loioa3e154f084f21015996d891a5e9d33d2 -->

# GRANT Object-Level Privilege Statement for Data Lake Relational Engine

Grants database object-level privileges on individual objects and schemasto a user or role.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT <object-level-privilege> [, …]
   ON { [ <owner>.]<object-name> | SCHEMA <schema-name> } 
   TO <user_role_schema> [, …]
   [ WITH GRANT OPTION ]
```



<a name="loioa3e154f084f21015996d891a5e9d33d2__grant_object_priv_parm1"/>

## Parameters

 *<user\_role\_schema\>*
 :   Must be the name of existing users, immutable roles, or schemas. Separate the list with commas.

  *<object-level-privilege\>*
 :   Specifies the object- or schema-level privilege being granted.

    ```
    <object-level-privilege> ::=
       ALL [ PRIVILEGES ] 
       | ALTER 
       | BACKUP TABLE
       | CREATE ANY**
       | DELETE 
       | DROP**
       | EXECUTE
       | EXECUTE PROCEDURE**
       | INSERT
       | LOAD
       | REFERENCES [ ( <column-name> [, …] ) ] 
       | RESTORE TABLE
       | SELECT [ ( <column-name> [, …] ) ] 
       | TRUNCATE
       | UPDATE [ ( <column-name>, …) ]
       | USAGE*
    
    **CREATE ANY, DROP, and EXECUTE PROCEDURE are only supported by SCHEMA <schema-name>
    *USAGE is only supported by [ <owner>.]<object-name>
    ```

    Object-level privilege can be granted on a specific object or on a schema. When granted on a specific object, the privilege applies only to that object. When grant on a schema, the privilege applies to any object within the schema.


    <table>
    <tr>
    <th valign="top">

    Object Privilege


    
    </th>
    <th valign="top">

    Supported Object Types


    
    </th>
    <th valign="top">

    Description


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    ALL


    
    </td>
    <td valign="top">

    -   All


    
    </td>
    <td valign="top">

    -   Grants ALTER, BACKUP TABLE, DELETE, INSERT, REFERENCES, RESTORE TABLE, SELECT, TRUNCATE, and UPDATE privileges on tables.
    -   Grants DELETE, INSERT, LOAD and UPDATE privileges on views.
    -   Grants ALTER, DELET, SELECT, and TRUNCTATE on materialized views.
    -   Grants REFERENCES on indexes.
    -   Grants ALTER, CREATE ANY, DELETE, DROP, EXECUTE, INSERT, LOAD, REFERENCES, REFRESH, SELECT, TRUNCATE, and UPDATE on schemas.
    -   Grants EXECUTE on procedures and functions.
    -   Grants USAGE on sequences.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ALTER


    
    </td>
    <td valign="top">

    -   Tables
    -   Materialized views
    -   Schemas


    
    </td>
    <td valign="top">

    User can alter the named table or materialized view.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    BACKUP TABLE


    
    </td>
    <td valign="top">

    -   Tables
    -   Schemas


    
    </td>
    <td valign="top">

    User can backup the named table, regardless of table ownership. Additional BACKUP TABLE system privileges are required to backup a table. See [BACKUP TABLE Statement for Data Lake Relational Engine](backup-table-statement-for-data-lake-relational-engine-5c2f08f.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    CREATE ANY<sup>\*\*</sup>


    
    </td>
    <td valign="top">

    -   Schemas


    
    </td>
    <td valign="top">

    User can create any object type supported by schemas in the named schema.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    DELETE


    
    </td>
    <td valign="top">

    -   Tables
    -   Views
    -   Schemas


    
    </td>
    <td valign="top">

    User can delete rows from the named table or view.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    DROP<sup>\*\*</sup>


    
    </td>
    <td valign="top">

    -   Schemas


    
    </td>
    <td valign="top">

    User can drop any objects that are part of the named schema.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    EXECUTE


    
    </td>
    <td valign="top">

    -   Procedures
    -   Functions


    
    </td>
    <td valign="top">

    User can execute the named procedure or function.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    EXECUTE PROCEDURE<sup>\*\*</sup>


    
    </td>
    <td valign="top">

    -   Schemas


    
    </td>
    <td valign="top">

    User can execute procedures and functions owned by the schema.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    INSERT


    
    </td>
    <td valign="top">

    -   Tables
    -   Views
    -   Schemas


    
    </td>
    <td valign="top">

    User can insert rows into the named table or view.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    LOAD


    
    </td>
    <td valign="top">

    -   Tables
    -   Views
    -   Schemas


    
    </td>
    <td valign="top">

    User can load data into the named table or view.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    REFERENCES


    
    </td>
    <td valign="top">

    -   Tables
    -   Index
    -   Schemas


    
    </td>
    <td valign="top">

    User can create indexes and foreign keys on the named table or view. If column names are specified, then the user can only see those columns. Columns can only be specified on a table, not an indexor schema.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    SELECT


    
    </td>
    <td valign="top">

    -   Tables
    -   View
    -   Materialized Views
    -   Schemas


    
    </td>
    <td valign="top">

    User can look at information in a named table, view or materialized view. If column names are specified, then the user only sees information in the specified columns. Columns can only be specified on a table, not on a view,materialized view, or schema.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    RESTORE TABLE


    
    </td>
    <td valign="top">

    -   Tables
    -   Schemas


    
    </td>
    <td valign="top">

    User can restore the named table, regardless of table ownership. Additional RESTORE TABLE system privileges are required to restore a table. See [RESTORE TABLE Statement for Data Lake Relational Engine](restore-table-statement-for-data-lake-relational-engine-a407d96.md)


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    TRUNCATE


    
    </td>
    <td valign="top">

    -   Table
    -   Materialized View
    -   Schemas


    
    </td>
    <td valign="top">

    User can truncate the named table or materialized view.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    UPDATE


    
    </td>
    <td valign="top">

    -   Tables
    -   Views
    -   Schemas


    
    </td>
    <td valign="top">

    User can update rows in the named view or table. If column names are specified, then the user can update only those columns. Columns can only be named on a table, not on a viewor schema. To update a table, users must have both SELECT and UPDATE privilege on the table.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    USAGE<sup>\*</sup>


    
    </td>
    <td valign="top">

    -   Sequences


    
    </td>
    <td valign="top">

    User can evaluate the current or next value in a sequence.


    
    </td>
    </tr>
    </table>
    
  *<object-name\>*
 :   Specifies the type of object the privilege applies to.

    ```
    <object-name> ::=
       <table_name>
       | <view_name>
       | {<procedure-name> | <user-defined-function-name>}
       | <sequence_name>
    ```

  WITH GRANT OPTION
 :   The named user, role, or schema is also given privileges to grant the same privileges to other user, role, or schema.

 

<a name="loioa3e154f084f21015996d891a5e9d33d2__grant_object_priv_remarks1"/>

## Remarks

Some object-level privileges support a per column clause when being granted on a table. This will not be the case for schema-level privileges. For example, for a table you can grant SELECT on a specific column using GRANT SELECT ON T\(c1\) TO user.

A database schema is a way to logically group objects, but not all objects support schema. For more information, see [Objects Supporting Schemas](objects-supporting-schemas-b9403c8.md).

If the user is granted a privilege on one of the objects in the schema directly as opposed to on the schema itself and the privilege is granted with the WITH GRANT OPTION, then the re-grant of the privilege to another user is limited to the object. The privilege cannot be re-granted on the schema containing the object. For example, table1 is in schema1. User1 is granted SELECT on table1 with WITH GRANT OPTION. User1 can re-grant SELECT on table1 to user2, but cannot re-grant SELECT on schema1, which contains table1.



<a name="loioa3e154f084f21015996d891a5e9d33d2__grant_objects_privileges1"/>

## Privileges



### 

To grant the BACKUP TABLE object-level privilege requires one of:

-   BACKUP OWNER TABLE or BACKUP ANY TABLE system privilege if you own the table.
-   BACKUP ANY TABLE system privilege granted with the WITH ADMIN option if the table is owned by another user.
-   BACKUP TABLE object-level privilege granted with the WITH GRANT option on the table being backed up regardless of ownership.
-   BACKUP OWNER TABLE system privilege plus BACKUP TABLE object-level privilege granted with the WITH GRANT option on the schema that contains the table being backed up if the schema is owned by another user.

To grant the RESTORE TABLE object-level privilege requires one of:

-   RESTORE OWNER TABLE or RESTORE ANY TABLE system privilege if you own the table.
-   RESTORE ANY TABLE system privilege if the table is owned by another user.
-   RESTORE TABLE object-level privilege granted with the WITH GRANT option on the table being restored regardless of ownership.
-   RESTORE OWNER TABLE system privilege plus RESTORE TABLE object-level privilege granted with the WITH GRANT option on the schema to contain the table being restored if the schema is owned by another user.

To grant any other object-level privilege requires one of:

-   You own the object.
-   You have the MANAGE ANY OBJECT PRIVILEGE system privilege.
-   You have been granted the specific object-level privilege with the WITH GRANT OPTION clause on the object if the object is owned by another user.
-   You have been granted the specific object-level privilege with the WITH GRANT OPTION clause on the schema containing the object if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) and [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance granting privileges.



<a name="loioa3e154f084f21015996d891a5e9d33d2__grant_object_priv_standards1"/>

## Standards

-   SQL – syntax is an entry-level feature
-   SAP database products – supported by SAP Adaptive Server Enterprise

**Related Information**  


[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

