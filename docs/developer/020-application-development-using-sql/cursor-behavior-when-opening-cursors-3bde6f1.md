<!-- loio3bde6f116c5f1014a303f33133f65ba5 -->

# Cursor Behavior When Opening Cursors

You can configure the isolation level and duration of a cursor when you open it.

Isolation level
:   You can explicitly set the isolation level of operations on a cursor to be different from the current isolation level of the transaction. To do this, set the isolation\_level option.

Duration
:   By default, cursors in Embedded SQL close at the end of a transaction. Opening a cursor WITH HOLD allows you to keep it open until the end of a connection, or until you explicitly close it. ADO.NET, ODBC, JDBC, and Open Client leave cursors open at the end of transactions by default.

