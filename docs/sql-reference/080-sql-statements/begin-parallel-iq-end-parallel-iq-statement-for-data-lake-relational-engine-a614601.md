<!-- loioa614601884f21015b474d353173fad17 -->

# BEGIN PARALLEL IQ … END PARALLEL IQ Statement for Data Lake Relational Engine 

Groups `CREATE INDEX` statements together for execution at the same time.



<a name="loioa614601884f21015b474d353173fad17__section_azh_5fj_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
... BEGIN PARALLEL IQ <statement-list>
... END PARALLEL IQ;
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa614601884f21015b474d353173fad17__begin_parallel_parameters1"/>

## Parameters


<dl>
<dt><b>

*<statement-list\>*

</b></dt>
<dd>

A list of `CREATE INDEX` statements



</dd>
</dl>



<a name="loioa614601884f21015b474d353173fad17__begin_parallel_remarks1"/>

## Remarks

The `BEGIN PARALLEL IQ … END PARALLEL IQ` statement lets you execute a group of `CREATE INDEX` statements as though they are a single DDL statement, creating indexes on multiple IQ tables at the same time. While this statement is executing, you and other users cannot issue other DDL statements.

> ### Note:  
> This statement does not support text indexes.



<a name="loioa614601884f21015b474d353173fad17__begin_parallel_privileges1"/>

## Privileges



### 

None



<a name="loioa614601884f21015b474d353173fad17__begin_parallel_sideefects1"/>

## Side Effects

Automatic commit



<a name="loioa614601884f21015b474d353173fad17__begin_paralel_standards1"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise. For support of statements inside the statement, see *CREATE INDEX Statement*.



<a name="loioa614601884f21015b474d353173fad17__begin_parallel_examples1"/>

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


[BEGIN PARALLEL IQ … END PARALLEL IQ Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/6632c2b487bf49449b7652a9e3bce605.html "Groups CREATE INDEX statements together for execution at the same time.") :arrow_upper_right:

[CREATE INDEX Statement for Data Lake Relational Engine](create-index-statement-for-data-lake-relational-engine-a617ca4.md "Creates an index on a specified table, or pair of tables. Once an index is created, it is never referenced in a SQL statement again except to delete it using the DROP INDEX statement.")

