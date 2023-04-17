<!-- loio3bdebf766c5f1014af4fe71c8bc5e43b -->

# Cursors and Transactions

In general, a cursor closes when a COMMIT is performed.

There are two exceptions to this behavior:

-   The close\_on\_endtrans database option is set to Off.

-   A cursor is opened WITH HOLD, which is the default with Open Client and JDBC.


If either of these two cases is true, the cursor stays open on a COMMIT.



## ROLLBACK and Cursors

If a transaction rolls back, then cursors close except for those cursors opened WITH HOLD. However, don't rely on the contents of any cursor after a rollback.

The draft ISO SQL3 standard states that on a rollback, all cursors \(even those cursors opened WITH HOLD\) should close. You can obtain this behavior by setting the ansi\_close\_cursors\_on\_rollback option to On.



## Savepoints

If a transaction rolls back to a savepoint, and if the ansi\_close\_cursors\_on\_rollback option is On, then all cursors \(even those cursors opened WITH HOLD\) opened after the SAVEPOINT close.



## Cursors and Isolation Levels

You can change the isolation level of a connection during a transaction using the SET OPTION statement to alter the isolation\_level option. However, this change does not affect open cursors.

A snapshot of all rows committed at the snapshot start time is visible when the WITH HOLD clause is used with the snapshot, statement-snapshot, and readonly-statement-snapshot isolation levels. Also visible are all modifications completed by the current connection since the start of the transaction within which the cursor was open.

