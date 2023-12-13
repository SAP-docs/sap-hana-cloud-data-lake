<!-- loioa620cc1c84f21015bb14de905cb82ea7 -->

# LOCK TABLE Statement for Data Lake Relational Engine

Prevents other concurrent transactions from accessing or modifying a table within the specified time or lock released by earlier transaction.



<a name="loioa620cc1c84f21015bb14de905cb82ea7__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1 - Exclusively for multiplex coordinator nodes:

</b></dt>
<dd>

```
LOCK TABLE <table-list> [ WITH HOLD ] 
   IN { SHARE | WRITE | EXCLUSIVE } MODE [  WAIT <time> ];
```



</dd><dt><b>

**Syntax 2 - Exclusively for multiplex writer nodes:**

</b></dt>
<dd>

```
LOCK TABLE <table-name>
   IN WRITE MODE [ WAIT <time> ];
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa620cc1c84f21015bb14de905cb82ea7__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<table-name\>*

</b></dt>
<dd>

Must be a base table, not a view.

```
<table-list> ::=
   [ <owner>.]<table-name> [,...];
```



</dd><dt><b>

WRITE

</b></dt>
<dd>

WRITE mode is only valid for data lake Relational Engine base tables. LOCK TABLE either locks all tables in the *<table list\>* or none. If obtaining a lock for a multiplex write server, or when obtaining SHARE or EXCLUSIVE locks, you may only specify a single table. Standard data lake Relational Engine object qualification rules are used to parse *<table-name\>*.



</dd><dt><b>

WITH HOLD

</b></dt>
<dd>

The lock is held until the end of the connection. If the clause is not specified, the lock is released when the current transaction is committed or rolled back. Using the WITH HOLD clause in the same statement with WRITE MODE is unsupported and returns the error Must be a base table, not a view. WRITE mode is only valid for data lake Relational Engine base tables. ***SQLCODE=-131, ODBC 3 State="42000"***.



</dd><dt><b>

SHARE

</b></dt>
<dd>

Prevents other transactions from modifying the table, but allows them read access. In this mode, you can change data in the table as long as no other transaction has locked the row being modified, either indirectly, or explicitly by using `LOCK TABLE`.

> ### Note:  
> SHARE mode is supported only on multiplex coordinator nodes.



</dd><dt><b>

WRITE

</b></dt>
<dd>

Prevents other transactions from modifying a list of tables. Unconditionally commits the connections outermost transaction. The transaction’s snapshot version is established not by the `LOCK TABLE IN WRITE MODE` statement, but by the execution of the next command processed by data lake Relational Engine.

WRITE mode locks are released when the transaction commits or rolls back, or when the connection disconnects.

> ### Note:  
> -   WRITE mode is supported on multiplex Coordinator as well as Writer nodes.
> -   When the lock mode is set to WRITE – specifying the <code>[ WAIT <i class="varname">&lt;time&gt;</i> ]</code> clause is mandatory.



</dd><dt><b>

EXCLUSIVE

</b></dt>
<dd>

Prevents other transactions from accessing the table. Locks all views referencing the table. In this mode, no other transaction can execute queries, updates of any kind, or any other action against the table.

> ### Note:  
> EXCLUSIVE mode is supported only for multiplex coordinator nodes.



</dd><dt><b>

WAIT *<time\>*

</b></dt>
<dd>

Specifies maximum blocking time for all lock types. This clause is mandatory when lock mode is WRITE. When a time argument is given, the server locks the specified tables only if available within the specified time. The time argument can be specified in the format hh:nn:ss:sss. If a date part is specified, the server ignores it and converts the argument into a timestamp. When no time argument is given, the server waits indefinitely until a WRITE lock is available or an interrupt occurs.

> ### Note:  
> It is mandatory to specify the '<code>[ WAIT <i class="varname">&lt;time&gt;</i> ]</code>' clause when the lock mode is set to WRITE.



</dd>
</dl>



<a name="loioa620cc1c84f21015bb14de905cb82ea7__IQ_Usage"/>

## Remarks

-   Running `LOCK TABLE` holds the lock only on a single table per connection – running it consecutively on another table from this connection will automatically release the lock on the previous table and apply the lock on the current table.

    In the following example, `LOCK TABLE` holds the WRITE lock on the `Customers` table, and automatically releases the table lock acquired earlier on the `Employees` table:

    ```
    LOCK TABLE Employees IN WRITE MODE WAIT
    LOCK TABLE Customers IN WRITE MODE WAIT;
    ```

-   `LOCK TABLE` statements run on tables in the data lake data lake Relational Engine main store on the coordinator do not affect access to those tables from connections on secondary servers. For example, on a coordinator connection, issue the command:

    ```
    LOCK TABLE coord1 WITH HOLD IN EXCLUSIVE MODE;
    ```

    Note that when the command above runs on table `coord1` from the coordinator, you can access it from secondary nodes, that is, the `select` query works fine. However, you cannot modify `coord1`, and running an `insert` query returns the error: `table 'coord1' not found`. To sum it up, you can access `coord1` but modifying it throws an error.

    -   `sp_iqlocks` on the coordinator confirms that the table `coord1` has an exclusive \(E\) lock.

        The result of `sp_iqlocks` run on a connection on a secondary server does not show the exclusive lock on table `coord1`. The user on this connection can see updates to table `coord1` on the coordinator.

        Other connections on the coordinator can see the exclusive lock on table `coord1` and attempting to select from table `coord1` from another connection on the coordinator returns ***User DBA has the row in coord1 locked.***


-   `LOCK TABLE <table> IN EXCLUSIVE MODE` locks all views referencing the table.

-   The Transact-SQL \(T-SQL\) stored procedure dialect does not support `LOCK TABLE`. For example, this statement returns ***Syntax error near LOCK***:

    ```
    CREATE PROCEDURE tproc()
    AS
    BEGIN
    COMMIT;
    LOCK TABLE t1 IN SHARE MODE
    INSERT INTO t1 VALUES(30)
    END;
    ```

-   The Watcom-SQL stored procedure dialect supports `LOCK TABLE`. The default command delimiter is a semicolon \(;\). For example:

    ```
    CREATE PROCEDURE tproc()
    AS
    BEGIN
    COMMIT;
    LOCK TABLE t1 IN SHARE MODE
    INSERT INTO t1 VALUES(30)
    END;
    ```




<a name="loioa620cc1c84f21015bb14de905cb82ea7__IQ_Permissions"/>

## Privileges

The privilege varies by lock mode.


<table>
<tr>
<th valign="top">

Mode

</th>
<th valign="top">

Privilege Required

</th>
</tr>
<tr>
<td valign="top">

Share mode

</td>
<td valign="top">

Requires one of:

-   You own the table
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the table



</td>
</tr>
<tr>
<td valign="top">

Exclusive mode

</td>
<td valign="top">

Requires one of:

-   You own the table
-   ALTER ANY OBJECT system privilege
-   ALTER ANY TABLE system privilege
-   ALTER object-level privilege on the table



</td>
</tr>
</table>

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges.



<a name="loioa620cc1c84f21015bb14de905cb82ea7__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar



<a name="loioa620cc1c84f21015bb14de905cb82ea7__IQ_Examples"/>

## Examples

-   This example obtains a WRITE lock on the `Customers` and `Employees` tables, if available within 5 minutes and 3 seconds:

    ```
    LOCK TABLE Customers, Employees IN WRITE MODE WAIT
    '00:05:03';
    ```

-   This example waits indefinitely until the WRITE lock on the `Customers` and `Employees` tables is available, or an interrupt occurs:

    ```
    LOCK TABLE Customers, Employees IN WRITE MODE WAIT;
    ```

-   This example holds a WRITE lock on the `Customers` table and automatically releases the table lock acquired earlier on the `Employees` table:

    ```
    LOCK TABLE Employees IN WRITE MODE WAIT
    LOCK TABLE Customers IN WRITE MODE WAIT;
    ```


**Related Information**  


[SELECT Statement for Data Lake Relational Engine](select-statement-for-data-lake-relational-engine-a624e72.md "Retrieves information from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

