<!-- loio3be12d4e6c5f1014b1ea958cfeafa6c1 -->

# Structure of Embedded SQL Programs

SQL statements are placed \(embedded\) within regular C or C++ code. All Embedded SQL statements start with the words EXEC SQL and end with a semicolon \(;\).

Normal C language comments are allowed in the middle of Embedded SQL statements.

Every C program using Embedded SQL must contain the following statement before any other Embedded SQL statements in the source file.

```
EXEC SQL INCLUDE SQLCA;
```

Every C program using Embedded SQL must initialize a SQLCA first:

```
db_init( &sqlca );
```

One of the first Embedded SQL statements executed by the C program must be a CONNECT statement. The CONNECT statement is used to establish a connection with the database server and to specify the user ID that is used for authorizing all statements executed during the connection.

Some Embedded SQL statements do not generate any C code, or do not involve communication with the database. These statements are allowed before the CONNECT statement. Most notable are the INCLUDE statement and the WHENEVER statement for specifying error processing.

Every C program using Embedded SQL must finalize any SQLCA that has been initialized.

```
db_fini( &sqlca );
```

