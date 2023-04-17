<!-- loio3bde7ea26c5f1014ad9d911f73ac2c5f -->

# Multiple-row Fetching

Multiple-row fetching should not be confused with prefetching rows. Multiple row fetching is performed by the application, while prefetching is transparent to the application, and provides a similar performance gain.

Fetching multiple rows at a time can improve performance.

Some interfaces provide methods for fetching more than one row at a time into the next several fields in an array. Generally, the fewer separate fetch operations you execute, the fewer individual requests the server must respond to, and the better the performance. A modified FETCH statement that retrieves multiple rows is also sometimes called a **wide fetch**. Cursors that use multiple-row fetches are sometimes called **block cursors** or **fat cursors**.



## Using Multiple-Row Fetching

-   In ODBC, you can set the number of rows that are returned on each call to SQLFetchScroll or SQLExtendedFetch by setting the SQL\_ATTR\_ROW\_ARRAY\_SIZE or SQL\_ROWSET\_SIZE attribute.

-   In Embedded SQL, the FETCH statement uses an ARRAY clause to control the number of rows fetched at a time.

-   Open Client and JDBC do not support multi-row fetches. They do use prefetching.


