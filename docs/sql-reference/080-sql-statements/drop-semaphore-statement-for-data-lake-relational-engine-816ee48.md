<!-- loio816ee4806ce210149b77f9b71e10b229 -->

# DROP SEMAPHORE Statement for Data Lake Relational Engine

Drops a semaphore.



<a name="loio816ee4806ce210149b77f9b71e10b229__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP SEMAPHORE [ IF EXISTS ] [ <owner>.]<semaphore-name>
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

IF EXISTS clause

</b></dt>
<dd>

Use this clause to drop a semaphore only if it exists. If a semaphore does not exist and this clause is specified, then nothing happens and no error is returned.



</dd>
</dl>



## Remarks

An error is returned to any connection that is waiting to decrement the semaphore.



<a name="loio816ee4806ce210149b77f9b71e10b229__section_srd_sdy_m2b"/>

## Privileges

Requires one of:

-   You own the semaphore
-   DROP ANY MUTEX SEMAPHORE system privilege

For a temporary semaphore, you must be the connection that created the mutex.

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

The following statement drops a semaphore called license\_counter:

```
DROP SEMAPHORE license_counter;
```

**Related Information**  


[CREATE SEMAPHORE Statement for Data Lake Relational Engine](create-semaphore-statement-for-data-lake-relational-engine-816c77e.md "Creates or replaces a semaphore and establishes the initial value for its counter. A semaphore is a locking mechanism that uses a counter to communicate and control the availability of a resource such as an external library or procedure.")

[WAITFOR SEMAPHORE Statement for Data Lake Relational Engine](waitfor-semaphore-statement-for-data-lake-relational-engine-81803f2.md "Decrements the counter associated with a semaphore.")

[NOTIFY SEMAPHORE Statement for Data Lake Relational Engine](notify-semaphore-statement-for-data-lake-relational-engine-8171dbe.md "Increments the counter associated with a semaphore.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

