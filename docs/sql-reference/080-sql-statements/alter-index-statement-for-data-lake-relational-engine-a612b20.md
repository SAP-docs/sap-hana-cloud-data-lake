<!-- loioa612b20e84f21015b756a29e4fc11d93 -->

# ALTER INDEX Statement for Data Lake Relational Engine

Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.



<a name="loioa612b20e84f21015b756a29e4fc11d93__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER { INDEX <index-name> | [ INDEX ] FOREIGN KEY <role-name> | [ INDEX ] PRIMARY KEY }
   ON [ { <owner> | <schema-name> }.]<table-name>
     [ RENAME { TO | AS } <new-name> ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa612b20e84f21015b756a29e4fc11d93__alter_index_parameters1"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

Specifies the name of the table that contains the index or foreign key to rename.



</dd><dt><b>

RENAME TO | AS *<new-name\>*

</b></dt>
<dd>

Specifies the new name of the index or foreign key role.



</dd>
</dl>



<a name="loioa612b20e84f21015b756a29e4fc11d93__alter_index_remarks1"/>

## Remarks

Attempts to alter an index in a local temporary table return the error ***index not found***. Attempts to alter a nonuser-created index, such as a default index \(FP\), return the error ***Cannot alter index. Only indexes in base tables or global temporary tables with an owner type of USER can be altered.***



<a name="loioa612b20e84f21015b756a29e4fc11d93__alter_index_privilege1"/>

## Privileges



### 

Requires one of:

-   You own the underlying table of the index
-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   ALTER object-level privilege on the table
-   REFERENCES object-level privilege on the table
-   ALTER object-level privilege on the schema containing the table if the schema is owned by another user.



<a name="loioa612b20e84f21015b756a29e4fc11d93__alter_index_sideeffects1"/>

## Side Effects

Automatic commit. Clears the Results tab in the Results pane in Interactive SQL. Closes all cursors for the current connection.



<a name="loioa612b20e84f21015b756a29e4fc11d93__alter_index_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa612b20e84f21015b756a29e4fc11d93__alter_index_examples1"/>

## Examples

-   The following example renames an index COL1\_HG\_OLD in the table jal.mytable to COL1\_HG\_NEW:

    ```
    ALTER INDEX COL1_HG_OLD ON jal.mytable 
    RENAME AS COL1_HG_NEW;
    ```

-   The following example renames a foreign key role name ky\_dept\_id in table dba.Employees to emp\_dept\_id:

    ```
    ALTER INDEX FOREIGN KEY ky_dept_id
    ON dba.Employees 
    RENAME TO emp_dept_id;
    ```


**Related Information**  


[CREATE INDEX Statement for Data Lake Relational Engine](create-index-statement-for-data-lake-relational-engine-a617ca4.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[ALTER TABLE Statement for Data Lake Relational Engine](alter-table-statement-for-data-lake-relational-engine-39f1ec0.md "Modifies a table definition.")

[CREATE TABLE Statement for Data Lake Relational Engine](create-table-statement-for-data-lake-relational-engine-a619764.md "Creates a new table in the database or on a remote server.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[DROP INDEX Statement for Data Lake Relational Engine](drop-index-statement-for-data-lake-relational-engine-82d6c17.md "Removes an index from the database.")

[ALTER INDEX Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/daf745a457cc4f3ba56275c28dc14929.html "Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.") :arrow_upper_right:

