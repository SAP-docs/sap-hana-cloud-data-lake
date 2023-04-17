<!-- loio3be381786c5f10148341dc51f0a42e7c -->

# Transaction Processing

You can use the SATransaction object to group statements together. Each transaction ends with a call to the Commit method, which either makes your changes to the database permanent, or the Rollback method, which cancels all the operations in the transaction.

Once the transaction is complete, you must create a new SATransaction object to make further changes. This behavior is different from ODBC and Embedded SQL, where a transaction persists after you execute a COMMIT or ROLLBACK until the transaction is closed.

If you do not create a transaction, the .NET Data Provider operates in autocommit mode by default. There is an implicit COMMIT after each insert, update, or delete, and once an operation is completed, the change is made to the database. In this case, the changes cannot be rolled back.



## Isolation Level Settings for Transactions

The database isolation level is used by default for transactions. You can choose to specify the isolation level for a transaction using the IsolationLevel property when you begin the transaction. The isolation level applies to all statements executed within the transaction. The .NET Data Provider supports snapshot isolation.

The locks that the database server uses when you execute a SQL statement depend on the transaction's isolation level.



## Distributed Transaction Processing

The .NET 2.0 framework introduced a new namespace System.Transactions, which contains classes for writing transactional applications. Client applications can create and participate in distributed transactions with one or multiple participants. Client applications can implicitly create transactions using the TransactionScope class. The connection object can detect the existence of an ambient transaction created by the TransactionScope and automatically enlist. The client applications can also create a CommittableTransaction and call the EnlistTransaction method to enlist. This feature is supported by the .NET Data Provider. Distributed transaction has significant performance overhead. Use database transactions for non-distributed transactions.



## C\# SATransaction Example

The following example shows how to wrap an INSERT into a transaction so that it can be committed or rolled back. A transaction is created with an SATransaction object and linked to the execution of a SQL statement using an SACommand object. Isolation level 2 \(RepeatableRead\) is specified so that other database users cannot update the row. The lock on the row is released when the transaction is committed or rolled back. If you do not use a transaction, the .NET Data Provider operates in autocommit mode and you cannot roll back any changes that you make to the database.

```
SAConnection conn = new SAConnection( 
    "Data Source=SAP IQ 17 Demo;Password="+pwd );
conn.Open();
string stmt = "UPDATE Products SET UnitPrice = 2000.00 " +
    "WHERE Name = 'Tee shirt'";
bool goAhead = false;

SATransaction trans = conn.BeginTransaction(SAIsolationLevel.RepeatableRead);
SACommand cmd = new SACommand(stmt, conn, trans);
int rowsAffected = cmd.ExecuteNonQuery();
if (goAhead)
    trans.Commit();
else
    trans.Rollback();
conn.Close();
```

