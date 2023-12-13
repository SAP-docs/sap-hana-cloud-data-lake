<!-- loio816c77ee6ce210148f098361bc9303f2 -->

# CREATE SEMAPHORE Statement for Data Lake Relational Engine

Creates or replaces a semaphore and establishes the initial value for its counter. A semaphore is a locking mechanism that uses a counter to communicate and control the availability of a resource such as an external library or procedure.



<a name="loio816c77ee6ce210148f098361bc9303f2__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE | TEMPORARY ] SEMAPHORE [ IF NOT EXISTS ] [ <owner>.]<semaphore-name>
   [ START WITH <initial-count> ];
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

The name of the semaphore. Specify a valid identifier in the CHAR database collation.



</dd><dt><b>

OR REPLACE clause

</b></dt>
<dd>

Use this clause to overwrite \(update\) the definition of a permanent semaphore of the same name, if one exists.

If the OR REPLACE clause is specified, and a semaphore with this name is in use at the time, then the statement returns an error.

You cannot use this clause with the TEMPORARY or IF NOT EXISTS clauses.



</dd><dt><b>

TEMPORARY clause

</b></dt>
<dd>

Use this clause to create a temporary semaphore.

Do not use this clause with the OR REPLACE clause.



</dd><dt><b>

IF NOT EXISTS clause

</b></dt>
<dd>

Use this clause to create a semaphore only if it doesn't already exist. If a semaphore exists with the same name and same lifespan \(permanent or temporary\), then nothing happens and no error is returned.

You cannot use this clause with the OR REPLACE clause.



</dd><dt><b>

START WITH clause

</b></dt>
<dd>

Use this clause to specify the initial value for the semaphore counter. If this clause is not specified, then *<initial-count\>* is set to 0.

*<initial-count\>* can be specified using a variable \(for example, `START WITH @initial-count`\).

If you set *<initial-count\>* to NULL, or if it is set to a variable and the variable value is NULL, the behavior is equivalent to not specifying the clause.



</dd>
</dl>



## Remarks

The CREATE SEMAPHORE statement creates a semaphore and establishes a counter for it. Each time a NOTIFY SEMAPHORE statement is executed, the counter for the associated semaphore is incremented. Each time a WAITFOR SEMAPHORE statement is executed, and assuming the current count is a positive integer, the counter for the associated semaphore is decremented.

Permanent and temporary mutexes and semaphores share the same namespace, therefore you cannot create two of these objects with the same name. Use of the OR REPLACE and IF NOT EXISTS clause can inadvertently cause an error related to naming. For example, if you have a permanent mutex, and you try to create a temporary semaphore with the same name, an error is returned even if you specify IF NOT EXISTS. Similarly, if you have a temporary semaphore, and you try to replace it with a permanent semaphore with the same name by specifying OR REPLACE, an error is returned because this is equivalent to attempting to create a second object with the same name.

Permanent semaphore definitions persist across database restarts. However, their count returns to *<initial-count\>* after a restart.

A temporary semaphore persists until the connection that created it is terminated, or until an explicit DROP operation is performed. If another connection is waiting for a temporary semaphore and the connection that created the temporary semaphore is terminated, then an error is returned to the waiting connection.

When replacing \(OR REPLACE clause\) a permanent semaphore, the old semaphore is deleted, and all connections waiting for the semaphore are notified.

If the OR REPLACE clause is specified, and a permanent semaphore with that name exists and connections are blocked waiting for the semaphore, the semaphore is still replaced. In this case, the waiting connections are unblocked and an error is returned to them indicating that the semaphore has been dropped. There is one exception however. If the replacement semaphore definition has identical settings, there is no impact to waiting connections.



## Privileges

Requires the CREATE ANY MUTEX SEMAPHORE system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

Automatic commit, but only for permanent semaphores.



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

The following statement creates a semaphore called license\_counter and sets its counter to 3:

```
CREATE SEMAPHORE license_counter START WITH 3;
```

**Related Information**  


[DROP SEMAPHORE Statement for Data Lake Relational Engine](drop-semaphore-statement-for-data-lake-relational-engine-816ee48.md "Drops a semaphore.")

[NOTIFY SEMAPHORE Statement for Data Lake Relational Engine](notify-semaphore-statement-for-data-lake-relational-engine-8171dbe.md "Increments the counter associated with a semaphore.")

[WAITFOR SEMAPHORE Statement for Data Lake Relational Engine](waitfor-semaphore-statement-for-data-lake-relational-engine-81803f2.md "Decrements the counter associated with a semaphore.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

