<!-- loio3bde76c46c5f10149d35fcbd1107c792 -->

# Row Fetching Through a Cursor

The simplest way of processing the result set of a query using a cursor is to loop through all the rows of the result set until there are no more rows.

You can accomplish this task by performing these steps:

1.  Declare and open the cursor \(Embedded SQL\), or execute a statement that returns a result set \(ODBC, JDBC, Open Client\) or SADataReader object \(ADO.NET\).

2.  Continue to fetch the next row until you get a `Row Not Found` error.

3.  Close the cursor.


The technique used to fetch the next row is dependent on the interface you use. For example:

ADO.NET
:   Use the SADataReader.Read method.

ODBC
:   SQLFetch, SQLExtendedFetch, or SQLFetchScroll advances the cursor to the next row and returns the data.

JDBC
:   The next method of the ResultSet object advances the cursor and returns the data.

Embedded SQL
:   The FETCH statement carries out the same operation.

Open Client
:   The ct\_fetch function advances the cursor to the next row and returns the data.

