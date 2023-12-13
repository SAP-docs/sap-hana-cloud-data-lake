<!-- loio81803f236ce210149660ddd29337c1c8 -->

# WAITFOR SEMAPHORE Statement for Data Lake Relational Engine

Decrements the counter associated with a semaphore.



<a name="loio81803f236ce210149660ddd29337c1c8__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
WAITFOR SEMAPHORE [<owner>.]<semaphore-name> 
   [ TIMEOUT <in-milliseconds> ]; 

```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

The owner of the semaphore.



</dd><dt><b>

*<semaphore-name\>*

</b></dt>
<dd>

The name of the semaphore.



</dd><dt><b>

TIMEOUT clause

</b></dt>
<dd>

Specify the duration of time, in milliseconds, to wait to decrement the counter associated with the semaphore. If this clause is not specified, then the connection waits indefinitely until the count can be decremented, or until an error is returned.

*<in-milliseconds\>* can be specified using a variable \(for example, `TIMEOUT @timeout-value`\). If *<in-milliseconds\>* is set to a variable and the variable is NULL, the behavior is equivalent to not specifying the clause.



</dd>
</dl>



## Remarks

The WAITFOR SEMAPHORE statement decrements the counter associated with the semaphore if it is not currently zero; otherwise, it blocks.

If the counter is a positive integer, then the counter is decremented by 1 and the statement completes.

If the counter is 0, then the connection waits until notified that the counter is a positive integer, or until the duration specified by the TIMEOUT clause passes, at which point an error is returned indicating the timeout. Connections are notified in first-in, first-out \(FIFO\) order of WAITFOR statement execution.

An error is returned if the current connection is identified during deadlock detection while waiting on the semaphore. An error is also returned if the semaphore is dropped.

If a connection that notified a semaphore is dropped or canceled, the counter increment persists.



<a name="loio81803f236ce210149660ddd29337c1c8__section_svv_gvx_m2b"/>

## Privileges

Requires one of:

-   You own the semaphore
-   UPDATE ANY MUTEX SEMAPHORE system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

None.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



## Example

The following statement creates a semaphore and sets its initial value to zero:

```
CREATE OR REPLACE SEMAPHORE DBA.gate START WITH 0;
```

The following statements define a stored procedure that waits on this semaphore. If the semaphore counter is not zero, it will decrement the counter and proceed. If the semaphore counter is zero, it wil block:

```
CREATE OR REPLACE PROCEDURE SemTest()
BEGIN
    WAITFOR SEMAPHORE DBA.gate;
    SELECT 'Waitfor done';
END;
```

The following statement calls the stored procedure. Execution will be delayed since the semaphore is initially zero and the stored procedure blocks. It will block until a NOTIFY SEMAPHORE statement is executed on another connection.

```
CALL SemTest;
```

Execute the following statement on a separate connection. It increments the semaphore by 1 and allows a blocked connection to proceed. If no connection is blocked, the next WAITFOR statement that references the semaphore will proceed without blocking.

```
NOTIFY SEMAPHORE DBA.gate INCREMENT BY 1;
```

Execute the following statement on a separate connection. It increments the semaphore by 2 and allows two blocked connections to proceed. If only one connection is blocked, the next WAITFOR statement that references the semaphore will proceed without blocking. If no connections are blocked, the next 2 WAITFOR statements that reference the semaphore will proceed without blocking.

```
NOTIFY SEMAPHORE DBA.gate INCREMENT BY 2;
```

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE SEMAPHORE Statement for Data Lake Relational Engine](create-semaphore-statement-for-data-lake-relational-engine-816c77e.md "Creates or replaces a semaphore and establishes the initial value for its counter. A semaphore is a locking mechanism that uses a counter to communicate and control the availability of a resource such as an external library or procedure.")

[DROP SEMAPHORE Statement for Data Lake Relational Engine](drop-semaphore-statement-for-data-lake-relational-engine-816ee48.md "Drops a semaphore.")

[NOTIFY SEMAPHORE Statement for Data Lake Relational Engine](notify-semaphore-statement-for-data-lake-relational-engine-8171dbe.md "Increments the counter associated with a semaphore.")

