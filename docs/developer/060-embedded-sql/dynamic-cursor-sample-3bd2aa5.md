<!-- loio3bd2aa5d6c5f1014b489850f38b44c74 -->

# Dynamic Cursor Sample

This sample demonstrates the use of cursors for a dynamic SQL SELECT statement.



The dynamic cursor sample program \(dcur\) allows the user to select a table to look at with the N command. The program then presents as much information from that table as fits on the screen.

When this program is run, it prompts for a connection string. The following is an example.

```
UID=HDLADMIN;PWD=sql;DBF=iqdemo.db
```

The C program with the Embedded SQL is located in the <code><i>%IQDIRSAMP17%</i>\SQLAnywhere\C</code> directory.

The dcur program uses the Embedded SQL interface function db\_string\_connect to connect to the database. This function provides the extra functionality to support the connection string that is used to connect to the database.

The open\_cursor routine first builds the SELECT statement

```
SELECT * FROM <table-name>
```

where *<table-name\>* is a parameter passed to the routine. It then prepares a dynamic SQL statement using this string.

The Embedded SQL DESCRIBE statement is used to fill in the SQLDA structure with the results of the SELECT statement.

> ### Note:  
> An initial guess is taken for the size of the SQLDA \(3\). If this is not big enough, the actual size of the SELECT list returned by the database server is used to allocate a SQLDA of the correct size.
> 
> The SQLDA structure is then filled with buffers to hold strings that represent the results of the query. The fill\_s\_sqlda routine converts all data types in the SQLDA to DT\_STRING and allocates buffers of the appropriate size.

A cursor is then declared and opened for this statement. The rest of the routines for moving and closing the cursor remain the same.

The fetch routine is slightly different: it puts the results into the SQLDA structure instead of into a list of host variables. The print routine has changed significantly to print results from the SQLDA structure up to the width of the screen. The print routine also uses the name fields of the SQLDA to print headings for each column.

