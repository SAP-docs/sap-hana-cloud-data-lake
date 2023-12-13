<!-- loio816c2a336ce21014a279eb2f6d47cbb0 -->

# CREATE MUTEX Statement for Data Lake Relational Engine

Creates or replaces a mutex \(lock\) that can be used to lock a resource such as a file or a procedure.



<a name="loio816c2a336ce21014a279eb2f6d47cbb0__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE | TEMPORARY ] MUTEX [ IF NOT EXISTS ] [ <owner>.]<mutex-name>
   [ SCOPE { CONNECTION | TRANSACTION } ];
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

The name of the mutex. Specify a valid identifier in the CHAR database collation.



</dd><dt><b>

OR REPLACE clause

</b></dt>
<dd>

Use this clause to overwrite \(update\) the definition of a permanent mutex of the same name, if one exists.

If the OR REPLACE clause is specified, and a mutex with this name is in use at the time, then the statement returns an error.

You cannot use this clause with the TEMPORARY or IF NOT EXISTS clauses.



</dd><dt><b>

TEMPORARY clause

</b></dt>
<dd>

Use this clause to create a temporary mutex.

Do not use this clause with the OR REPLACE clause.



</dd><dt><b>

IF NOT EXISTS clause

</b></dt>
<dd>

Use this clause to create a mutex only if it doesn't already exist. If a mutex exists with the same name, then nothing happens and no error is returned.

You cannot use this clause with the OR REPLACE clause.



</dd><dt><b>

SCOPE clause

</b></dt>
<dd>

Use this clause to specify whether the mutex applies to a transaction \(TRANSACTION\), or the connection \(CONNECTION\). If the SCOPE clause is not specified, then the default behavior is CONNECTION.



</dd>
</dl>



## Remarks

Permanent and temporary mutexes and semaphores share the same namespace; therefore, you cannot create two of these objects with the same name and owner. Use of the OR REPLACE and IF NOT EXISTS clause can inadvertently cause an error related to naming. For example, if you have a permanent mutex, and you try to create a temporary semaphore with the same name, an error is returned even if you specify IF NOT EXISTS. Similarly, if you have a temporary semaphore, and you try to replace it with a permanent semaphore with the same name by specifying OR REPLACE, an error is returned because this is equivalent to attempting to create a second object with the same name.

Permanent mutex definitions persist across database restarts. However, their state information \(locked or released\), does not.

A temporary mutex persists until the connection that created it is terminated, or until the mutex is dropped using a DROP MUTEX statement. If another connection is waiting for a temporary mutex and the connection that created the temporary mutex is terminated, then an error is returned to the waiting connection indicating that the mutex has been deleted.

CONNECTION scope mutexes are not automatically released other than when the connection is terminated.



<a name="loio816c2a336ce21014a279eb2f6d47cbb0__section_psl_wfz_m2b"/>

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



## Example

The following statement creates a connection scope mutex called protect\_my\_cr\_section to protect a critical section of a stored procedure.

```
CREATE MUTEX protect_my_cr_section SCOPE CONNECTION;
```

**Related Information**  


[DROP MUTEX Statement for Data Lake Relational Engine](drop-mutex-statement-for-data-lake-relational-engine-816e9ff.md "Drops the specified mutex.")

[LOCK MUTEX Statement for Data Lake Relational Engine](lock-mutex-statement-for-data-lake-relational-engine-8171b78.md "Locks a resource such as a file or system procedure using a predefined mutex.")

[RELEASE MUTEX Statement for Data Lake Relational Engine](release-mutex-statement-for-data-lake-relational-engine-8172a39.md "Releases the specified connection-scope mutex, if it is locked by the current connection.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

