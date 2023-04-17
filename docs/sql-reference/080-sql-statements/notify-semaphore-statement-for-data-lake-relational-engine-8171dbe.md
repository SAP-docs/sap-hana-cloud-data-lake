<!-- loio8171dbe36ce21014b0d594471fc5e8a3 -->

# NOTIFY SEMAPHORE Statement for Data Lake Relational Engine

Increments the counter associated with a semaphore.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
NOTIFY SEMAPHORE [<owner>.]<semaphore-name> 
   [ INCREMENT BY <number> ]

```



## Parameters

 *<owner\>*
 :   The owner of the semaphore.

  *<semaphore-name\>*
 :   The name of the semaphore.

  INCREMENT BY clause
 :   Specify a positive integer to indicate how much to increment the counter associated with the semaphore. If this clause is not specified, then the counter is incremented by 1.

    *<number\>* can be specified using a variable \(for example, ***INCREMENT BY @inc-number***\).

    If you set *<number\>*\] to NULL, or if it is set to a variable and the variable value is NULL, the behavior is equivalent to not specifying the clause.

 

## Remarks

If the counter is currently 0 at the time it is incremented, and one or more connections are blocked on a WAITFOR SEMAPHORE statement that uses this semaphore, the NOTIFY SEMAPHORE statement notifies each of the connections. Each blocked connection, in turn, unblocks if the counter value is not zero and decrements the counter value. If the counter value is decremented to zero, then the next blocked connection continues to block. Blocked connections are unblocked in first-in, first-out \(FIFO\) order.

If a connection that notified a semaphore is dropped or canceled, the counter increment persists.



<a name="loio8171dbe36ce21014b0d594471fc5e8a3__section_u4d_wvx_m2b"/>

## Privileges

Requires one of:

-   You own the semaphore
-   UPDATE ANY MUTEX SEMAPHORE system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



## Side Effects

None.



## Standards

 ANSI/ISO SQL Standard
 :   Not in the standard.

 

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


[CREATE SEMAPHORE Statement for Data Lake Relational Engine](create-semaphore-statement-for-data-lake-relational-engine-816c77e.md "Creates or replaces a semaphore and establishes the initial value for its counter. A semaphore is a locking mechanism that uses a counter to communicate and control the availability of a resource such as an external library or procedure.")

[DROP SEMAPHORE Statement for Data Lake Relational Engine](drop-semaphore-statement-for-data-lake-relational-engine-816ee48.md "Drops a semaphore.")

[WAITFOR SEMAPHORE Statement for Data Lake Relational Engine](waitfor-semaphore-statement-for-data-lake-relational-engine-81803f2.md "Decrements the counter associated with a semaphore.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

