<!-- loio816e9ff46ce21014965e931a4455dd54 -->

# DROP MUTEX Statement for Data Lake Relational Engine

Drops the specified mutex.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP MUTEX [ IF EXISTS ] [ <owner>.]<mutex-name>

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

IF EXISTS clause

</b></dt>
<dd>

Use this clause to drop a mutex only if it exists. If a mutex does not exist and this clause is specified, then nothing happens and no error is returned.



</dd>
</dl>



## Remarks

If the mutex is locked by another connection, the drop operation proceeds without blocking but the mutex will persist in the namespace until the mutex is released. Connections waiting on the mutex receive an error immediately indicating that the object has been dropped.



## Privileges

Requires the CREATE ANY MUTEX SEMAPHORE system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

Automatic commit, but only for permanent mutexes.



## Standards


<dl>
<dt><b>

ANSI/ISO SQL Standard

</b></dt>
<dd>

Not in the standard.



</dd>
</dl>



The following statement drops the protect\_my\_cr\_section mutex:

```
DROP MUTEX protect_my_cr_section;
```

**Related Information**  


[CREATE MUTEX Statement for Data Lake Relational Engine](create-mutex-statement-for-data-lake-relational-engine-816c2a3.md "Creates or replaces a mutex (lock) that can be used to lock a resource such as a file or a procedure.")

[LOCK MUTEX Statement for Data Lake Relational Engine](lock-mutex-statement-for-data-lake-relational-engine-8171b78.md "Locks a resource such as a file or system procedure using a predefined mutex.")

[RELEASE MUTEX Statement for Data Lake Relational Engine](release-mutex-statement-for-data-lake-relational-engine-8172a39.md "Releases the specified connection-scope mutex, if it is locked by the current connection.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

