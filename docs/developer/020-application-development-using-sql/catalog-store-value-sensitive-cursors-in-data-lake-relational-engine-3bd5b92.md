<!-- loio3bd5b9246c5f1014a0c9b05ccc602cd7 -->

# Catalog Store Value-sensitive Cursors in Data Lake Relational Engine 

For value-sensitive cursors, membership is insensitive, and the order and value of the result set is sensitive.

Value-sensitive cursors can be used for read-only or updatable cursor types.



## Standards

Value-sensitive cursors do not correspond to an ISO/ANSI standard definition. They correspond to ODBC keyset-driven cursors.



## Programming Interfaces


<table>
<tr>
<th valign="top">

Interface



</th>
<th valign="top">

Cursor Type



</th>
<th valign="top">

Comment



</th>
</tr>
<tr>
<td valign="top">

ODBC, ADO/OLE DB



</td>
<td valign="top">

Keyset-driven



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Embedded SQL



</td>
<td valign="top">

SCROLL



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

JDBC



</td>
<td valign="top">

INSENSITIVE and CONCUR\_UPDATABLE



</td>
<td valign="top">

With the SAP IQ JDBC driver, a request for an updatable INSENSITIVE cursor is answered with a value-sensitive cursor.



</td>
</tr>
<tr>
<td valign="top">

Open Client and jConnect



</td>
<td valign="top">

Not supported



</td>
<td valign="top">

 



</td>
</tr>
</table>



## Description

If the application fetches a row composed of a base underlying row that has changed, then the application must be presented with the updated value, and the SQL\_ROW\_UPDATED status must be issued to the application. If the application attempts to fetch a row that was composed of a base underlying row that was deleted, a SQL\_ROW\_DELETED status must be issued to the application.

Changes to primary key values remove the row from the result set \(treated as a delete, followed by an insert\). A special case occurs when a row in the result set is deleted \(either from cursor or outside\) and a new row with the same key value is inserted. This will result in the new row replacing the old row where it appeared.

There is no guarantee that rows in the result set match the query's selection or order specification. Since row membership is fixed at open time, subsequent changes that make a row not match the WHERE clause or ORDER BY do not change a row's membership nor position.

All values are sensitive to changes made through the cursor. The sensitivity of membership to changes made through the cursor is controlled by the ODBC option SQL\_STATIC\_SENSITIVITY. If this option is on, then inserts through the cursor add the row to the cursor. Otherwise, they are not part of the result set. Deletes through the cursor remove the row from the result set, preventing a hole returning the SQL\_ROW\_DELETED status.

Value-sensitive cursors use a **key set table**. When the cursor is opened, a work table is populated with identifying information for each row contributing to the result set. When scrolling through the result set, the key set table is used to identify the membership of the result set, but values are obtained, if necessary, from the underlying tables.

The fixed membership property of value-sensitive cursors allows your application to remember row positions within a cursor and be assured that these positions will not change.

-   If a row was updated or may have been updated since the cursor was opened, a SQLE\_ROW\_UPDATED\_WARNING is returned when the row is fetched. The warning is generated only once: fetching the same row again does not produce the warning.

    An update to any column of the row causes the warning, even if the updated column is not referenced by the cursor. For example, a cursor on Surname and GivenName would report the update even if only the Birthdate column was modified. These update warning and error conditions do not occur in bulk operations mode \(-b database server option\) when row locking is disabled.

-   An attempt to execute a positioned update or delete on a row that has been modified since it was last fetched returns a SQLE\_ROW\_UPDATED\_SINCE\_READ error and cancels the statement. An application must FETCH the row again before the UPDATE or DELETE is permitted.

    An update to any column of the row causes the error, even if the updated column is not referenced by the cursor. The error does not occur in bulk operations mode.

-   If a row has been deleted after the cursor is opened, either through the cursor or from another transaction, a **hole** is created in the cursor. The membership of the cursor is fixed, so a row position is reserved, but the DELETE operation is reflected in the changed value of the row. If you fetch the row at this hole, you receive a -197 SQLCODE error, indicating that there is no current row, and the cursor is left positioned on the hole. You can avoid holes by using sensitive cursors, as their membership changes along with the values.


Rows cannot be prefetched for value-sensitive cursors. This requirement may affect performance.



## Inserting Multiple Rows

When inserting multiple rows through a value-sensitive cursor, the new rows appear at the end of the result set.

