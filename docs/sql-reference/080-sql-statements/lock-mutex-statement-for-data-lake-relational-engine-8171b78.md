<!-- loio8171b78c6ce2101489eac0eed03b6321 -->

# LOCK MUTEX Statement for Data Lake Relational Engine

Locks a resource such as a file or system procedure using a predefined mutex.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
LOCK MUTEX [ <owner>.]<mutex-name> 
   [ IN { SHARE | EXCLUSIVE } MODE ] 
   [ TIMEOUT <in-milliseconds> ]

```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

*<owner\>*

</b></dt>
<dd>

The owner of the mutex.



</dd><dt><b>

*<mutex-name\>*

</b></dt>
<dd>

The name of the mutex.



</dd><dt><b>

IN \{ *SHARE* | *EXCLUSIVE* \} MODE clause

</b></dt>
<dd>

Use this clause to specify whether the lock provides exclusive access to the resource \(EXCLUSIVE\), or whether other connections can use the resource as well \(SHARE\). If the IN...MODE clause is not specified, then EXCLUSIVE is the default behavior.



</dd><dt><b>

TIMEOUT clause

</b></dt>
<dd>

The amount of time, in milliseconds \(greater than 0\), to wait to acquire the lock. If the TIMEOUT clause is not specified, then the connection waits indefinitely until the lock can be acquired.

*<in-milliseconds\>* can be specified using a variable \(for example, `TIMEOUT @timeout-value`\). If *<in-milliseconds\>* is set to a variable and the variable is NULL, the behavior is equivalent to not specifying the clause.



</dd>
</dl>



## Remarks

Recursive LOCK MUTEX statements are allowed; however, an equal number of releases \(RELEASE MUTEX\) are required to release the mutex for connection-scope mutexes.

If a connection executes the LOCK MUTEX statement in SHARE MODE, and then again in EXCLUSIVE MODE, it may be blocked if other connections have the mutex locked in SHARE MODE. If not, then the lock mode changes to an exclusive lock and remains that way until the lock is completely released by the connection.

For transaction-scope mutexes \(that is, the SCOPE TRANSACTION clause was specified at creation time\), the mutex is held until the end of the transaction. For connection-scope mutexes \(that is, the SCOPE CONNECTION clause was specified at creation time\), the mutex is held until a RELEASE MUTEX statement is executed, or the connection is terminated.

LOCK MUTEX statements benefit from the same deadlock detection used for table and row locks.



<a name="loio8171b78c6ce2101489eac0eed03b6321__section_gvx_3wx_m2b"/>

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



The following statement locks the protect\_my\_cr\_section mutex in exclusive mode:

```
LOCK MUTEX protect_my_cr_section IN EXCLUSIVE MODE;
```

**Related Information**  


[CREATE MUTEX Statement for Data Lake Relational Engine](create-mutex-statement-for-data-lake-relational-engine-816c2a3.md "Creates or replaces a mutex (lock) that can be used to lock a resource such as a file or a procedure.")

[DROP MUTEX Statement for Data Lake Relational Engine](drop-mutex-statement-for-data-lake-relational-engine-816e9ff.md "Drops the specified mutex.")

[RELEASE MUTEX Statement for Data Lake Relational Engine](release-mutex-statement-for-data-lake-relational-engine-8172a39.md "Releases the specified connection-scope mutex, if it is locked by the current connection.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

