<!-- loiodaf745a457cc4f3ba56275c28dc14929 -->

# ALTER INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.



## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected to SAP HANA database as a SAP HANA database user..



```
ALTER { INDEX <index-name> | [ INDEX ] FOREIGN KEY <role-name> | [ INDEX ] PRIMARY KEY }
   ON [ <schema-name>.]<table-name>
     [ RENAME { TO | AS } <new-name> ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiodaf745a457cc4f3ba56275c28dc14929__section_tkw_msk_sqb"/>

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



<a name="loiodaf745a457cc4f3ba56275c28dc14929__section_inp_4sk_sqb"/>

## Remarks

Attempts to alter an index in a local temporary table return the error ***index not found***. Attempts to alter a nonuser-created index, such as a default index \(FP\), return the error ***Cannot alter index. Only indexes in base tables or global temporary tables with an owner type of USER can be altered.***



<a name="loiodaf745a457cc4f3ba56275c28dc14929__section_irl_j1q_wwb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loiodaf745a457cc4f3ba56275c28dc14929__section_mcq_5sk_sqb"/>

## Side Effects

Automatic commit. Clears the Results tab in the Results pane in Interactive SQL. Closes all cursors for the current connection.



<a name="loiodaf745a457cc4f3ba56275c28dc14929__section_kmp_vsk_sqb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loiodaf745a457cc4f3ba56275c28dc14929__section_gpt_xsk_sqb"/>

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


[CREATE INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-afc9ba6.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[DROP INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](drop-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-52fb1c7.md "Removes an index from the database.")

[ALTER INDEX Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a612b20e84f21015b756a29e4fc11d93.html "Renames indexes in base or global temporary tables, foreign key role names of indexes and foreign keys explicitly created by a user, or changes the clustered nature of an index on a catalog store table. You can't rename indexes created to enforce key constraints.") :arrow_upper_right:

