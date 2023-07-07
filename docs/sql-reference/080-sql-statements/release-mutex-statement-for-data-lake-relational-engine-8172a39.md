<!-- loio8172a3926ce210148b4dcdf5a3f1c546 -->

# RELEASE MUTEX Statement for Data Lake Relational Engine

Releases the specified connection-scope mutex, if it is locked by the current connection.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
RELEASE MUTEX [ <owner>.]<mutex-name>

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



</dd>
</dl>



## Remarks

The RELEASE MUTEX statement releases one instance of lock on the mutex. So, if a connection has locked the mutex multiple times, then only one lock on the mutex is released per RELEASE MUTEX statement.

An error is returned if the mutex was not locked by the current connection or if the release is being requested for a transaction-scope mutex.

The RELEASE MUTEX statement will succeed on a dropped mutex that is locked by the current connection.



<a name="loio8172a3926ce210148b4dcdf5a3f1c546__section_arl_rvx_m2b"/>

## Privileges

Requires one of:

-   You own the mutex
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



The following statement releases the protect\_my\_cr\_section mutex:

```
RELEASE MUTEX protect_my_cr_section;
```

**Related Information**  


[CREATE MUTEX Statement for Data Lake Relational Engine](create-mutex-statement-for-data-lake-relational-engine-816c2a3.md "Creates or replaces a mutex (lock) that can be used to lock a resource such as a file or a procedure.")

[DROP MUTEX Statement for Data Lake Relational Engine](drop-mutex-statement-for-data-lake-relational-engine-816e9ff.md "Drops the specified mutex.")

[LOCK MUTEX Statement for Data Lake Relational Engine](lock-mutex-statement-for-data-lake-relational-engine-8171b78.md "Locks a resource such as a file or system procedure using a predefined mutex.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

