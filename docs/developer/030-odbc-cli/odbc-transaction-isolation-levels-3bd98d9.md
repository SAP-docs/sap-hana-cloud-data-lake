<!-- loio3bd98d9a6c5f10148433d2d4632dd453 -->

# ODBC Transaction Isolation Levels

You can use SQLSetConnectAttr to set the transaction isolation level for a connection.

The characteristics that determine the transaction isolation level that the software provides include the following:

SQL\_TXN\_READ\_UNCOMMITTED
:   Set isolation level to 0. When this attribute value is set, it isolates any data read from changes by others and changes made by others cannot be seen. The re-execution of the read statement is affected by others. This does not support a repeatable read. This is the default value for isolation level.

SQL\_TXN\_READ\_COMMITTED
:   Set isolation level to 1. When this attribute value is set, it does not isolate data read from changes by others, and changes made by others can be seen. The re-execution of the read statement is affected by others. This does not support a repeatable read.

SQL\_TXN\_REPEATABLE\_READ
:   Set isolation level to 2. When this attribute value is set, it isolates any data read from changes by others, and changes made by others cannot be seen. The re-execution of the read statement is affected by others. This supports a repeatable read.

SQL\_TXN\_SERIALIZABLE
:   Set isolation level to 3. When this attribute value is set, it isolates any data read from changes by others, and changes made by others cannot be seen. The re-execution of the read statement is not affected by others. This supports a repeatable read.

SA\_SQL\_TXN\_SNAPSHOT
:   Set isolation level to Snapshot. When this attribute value is set, it provides a single view of the database for the entire transaction.

SA\_SQL\_TXN\_STATEMENT\_SNAPSHOT
:   Set isolation level to Statement-snapshot. When this attribute value is set, it provides less consistency than Snapshot isolation, but may be useful when long running transactions result in too much space being used in the temporary file by the version store.

SA\_SQL\_TXN\_READONLY\_STATEMENT\_SNAPSHOT
:   Set isolation level to Readonly-statement-snapshot. When this attribute value is set, it provides less consistency than Statement-snapshot isolation, but avoids the possibility of update conflicts. Therefore, it is most appropriate for porting applications originally intended to run under different isolation levels.

The allow\_snapshot\_isolation database option must be set to On to use the Snapshot, Statement-snapshot, or Readonly-statement-snapshot settings.



The following fragment sets the isolation level to Snapshot:

```
SQLAllocHandle( SQL_HANDLE_DBC, env, &dbc );
SQLSetConnectAttr( dbc, SQL_ATTR_TXN_ISOLATION,
      SA_SQL_TXN_SNAPSHOT, SQL_IS_UINTEGER );
```

