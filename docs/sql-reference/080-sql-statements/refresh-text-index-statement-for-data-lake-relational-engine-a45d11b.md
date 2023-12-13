<!-- loioa45d11b684f210159fffb17b6e829901 -->

# REFRESH TEXT INDEX Statement for Data Lake Relational Engine

Refreshes a text index.



<a name="loioa45d11b684f210159fffb17b6e829901__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REFRESH TEXT INDEX <text-index-name> ON [ { <owner> | <schema-name> }.]<table-name>
   [ WITH { ISOLATION LEVEL <isolation-level> 
          | EXCLUSIVE MODE 
          | SHARE MODE } ]
   [ FORCE { BUILD | INCREMENTAL } ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa45d11b684f210159fffb17b6e829901__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

WITH

</b></dt>
<dd>

Use the WITH clause to specify what kind of locks to obtain on the underlying base tables during the refresh. The types of locks obtained determine how the text index is populated and how concurrency for transactions is affected. If you do not specify the WITH clause, the default is WITH ISOLATION LEVEL READ UNCOMMITTED, regardless of any isolation level set for the connection.

You can specify the following WITH clause options:

-   ISOLATION LEVEL *<isolation-level\>* – changes the isolation level for the execution of the refresh operation. The original isolation level of the connection is restored at the end of the statement execution.
-   EXCLUSIVE MODE – use if you do not want to change the isolation level, but want to guarantee that the data is updated to be consistent with committed data in the underlying table. When using WITH EXCLUSIVE MODE, exclusive table locks are placed on the underlying base table and no other transaction can execute queries, updates, or any other action against the underlying table\(s\) until the refresh operation is complete. If table locks cannot be obtained, the refresh operation fails and an error is returned.
-   SHARE MODE – use to give read access on the underlying table to other transactions while the refresh operation takes place. When this clause is specified, shared table locks are obtained on the underlying base table before the refresh operation is performed and are held until the refresh operation completes.



</dd><dt><b>

FORCE \{ BUILD | INCREMENTAL \}

</b></dt>
<dd>

Use this clause to specify the refresh method. If this clause is not specified, the database server decides whether to do an incremental update or a full rebuild based on how much of the table has changed:

-   FORCE BUILD – refreshes the text index by re-creating it. Use this clause to force a complete rebuild of the text index.
-   FORCE INCREMENTAL – refreshes the text index based only on what has changed in the underlying table. An incremental refresh takes less time to complete if there have not been a significant amount of updates to the underlying table. Use this clause to force an incremental update of the text index.

    An incremental refresh does not remove deleted entries from the text index. As a result, the size of the text index may be larger than expected to contain the current and historic data. Typically, this issue occurs with text indexes that are always manually refreshed with the FORCE INCREMENTAL clause. On automatically refreshed text indexes, historic data is automatically deleted when it makes up 50% of the total size of the text index.




</dd>
</dl>



<a name="loioa45d11b684f210159fffb17b6e829901__IQ_Usage"/>

## Remarks

This statement can only be used on text indexes defined as MANUAL REFRESH or AUTO REFRESH.

When using the FORCE clause, you can examine the results of the sa\_text\_index\_stats system procedure to decide whether a complete rebuild \(FORCE BUILD\), or incremental update \(FORCE INCREMENTAL\) is most appropriate.

You cannot execute the REFRESH TEXT INDEX statement on a text index that is defined as IMMEDIATE REFRESH.

For MANUAL REFRESH text indexes, use the sa\_text\_index\_stats system procedure to determine whether the text index should be refreshed. Divide pending\_length by doc\_length, and use the percentage as a guide for deciding whether a refresh is required. To determine the type of rebuild required, use the same process for deleted\_length and doc\_count.

This statement cannot be executed when there are cursors opened with the WITH HOLD clause that use either statement or transaction snapshots.



<a name="loioa45d11b684f210159fffb17b6e829901__IQ_Permissions"/>

## Privileges

Requires one of:

-   You own the underlying table of the index
-   CREATE ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY INDEX system privilege
-   ALTER ANY OBJECT system privilege
-   REFERENCES object-level privilege on the table
-   CREATE ANY or ALTER object-level privilege on the schema containing the indexed table if the schema is owned by another user.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa45d11b684f210159fffb17b6e829901__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa45d11b684f210159fffb17b6e829901__IQ_Examples"/>

## Examples

The following example refreshes a fictitious text index called `MarketingTextIndex`, forcing it to be rebuilt:

```
REFRESH TEXT INDEX MarketingTextIndex ON GROUPO.MarketingInformation 
    FORCE BUILD;
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

