<!-- loio6632c2b487bf49449b7652a9e3bce605 -->

# BEGIN PARALLEL IQ … END PARALLEL IQ Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Groups `CREATE INDEX` statements together for execution at the same time.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Executing SQL Statements](remote-execute-usage-examples-for-executing-sql-statements-fd99ac0.md).



```
... BEGIN PARALLEL IQ <statement-list>
... END PARALLEL IQ
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loio6632c2b487bf49449b7652a9e3bce605__section_cry_gbl_sqb"/>

## Parameters


<dl>
<dt><b>

*<statement-list\>*

</b></dt>
<dd>

A list of `CREATE INDEX` statements



</dd>
</dl>



<a name="loio6632c2b487bf49449b7652a9e3bce605__section_rkr_3bl_sqb"/>

## Remarks

The `BEGIN PARALLEL IQ … END PARALLEL IQ` statement lets you execute a group of `CREATE INDEX` statements as though they are a single DDL statement, creating indexes on multiple IQ tables at the same time. While this statement is executing, you and other users cannot issue other DDL statements.

> ### Note:  
> This statement does not support text indexes.



<a name="loio6632c2b487bf49449b7652a9e3bce605__section_wcq_ynq_wwb"/>

## Privileges



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio6632c2b487bf49449b7652a9e3bce605__section_uvn_kbl_sqb"/>

## Side Effects

Automatic commit



<a name="loio6632c2b487bf49449b7652a9e3bce605__section_lj5_lbl_sqb"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise. For support of statements inside the statement, see *CREATE INDEX Statement*.



<a name="loio6632c2b487bf49449b7652a9e3bce605__section_l5n_nbl_sqb"/>

## Examples

The following statement executes atomically. If one command fails, the entire statement rolls back:

```
BEGIN PARALLEL IQ
    CREATE HG INDEX c1_HG on table1 (col1);
    CREATE HNG INDEX c12_HNG on table1 (col12);
    CREATE HNG INDEX c2_HNG on table1 (col2);
END PARALLEL IQ
```

**Related Information**  


[Concurrent Column Indexing](https://help.sap.com/viewer/a8937bea84f21015a80bc776cf758d50/2023_1_QRC/en-US/a7233eb384f21015a814a783690486c0.html "In some cases, you can create more than one column index simultaneously.") :arrow_upper_right:

[CREATE INDEX Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-index-statement-for-data-lake-relational-engine-sap-hana-db-managed-afc9ba6.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

[BEGIN PARALLEL IQ … END PARALLEL IQ Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a614601884f21015b474d353173fad17.html "Groups CREATE INDEX statements together for execution at the same time.") :arrow_upper_right:

