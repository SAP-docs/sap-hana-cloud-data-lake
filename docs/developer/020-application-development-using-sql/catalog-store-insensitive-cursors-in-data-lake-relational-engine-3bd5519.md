<!-- loio3bd551916c5f1014ab92f20c2e2c1f73 -->

# Catalog Store Insensitive Cursors in Data Lake Relational Engine 

These cursors have insensitive membership, order, and values. No changes made after cursor open time are visible.

Insensitive cursors are used only for read-only cursor types.



## Standards

Insensitive cursors correspond to the ISO/ANSI standard definition of insensitive cursors, and to ODBC static cursors.



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

Static



</td>
<td valign="top">

If an updatable static cursor is requested, a value-sensitive cursor is used instead.



</td>
</tr>
<tr>
<td valign="top">

Embedded SQL



</td>
<td valign="top">

INSENSITIVE



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

JDBC



</td>
<td valign="top">

INSENSITIVE



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Open Client



</td>
<td valign="top">

Unsupported



</td>
<td valign="top">

 



</td>
</tr>
</table>



## Description

Insensitive cursors always return rows that match the query's selection criteria, in the order specified by any ORDER BY clause.

The result set of an insensitive cursor is fully materialized as a work table when the cursor is opened. This has the following consequences:

-   If the result set is very large, the space and memory requirements for managing the result set may be significant.

-   No row is returned to the application before the entire result set is assembled as a work table. For complex queries, this may lead to a delay before the first row is returned to the application.

-   Subsequent rows can be fetched directly from the work table, and so are returned quickly. The client library may prefetch several rows at a time, further improving performance.

-   Insensitive cursors are not affected by ROLLBACK or ROLLBACK TO SAVEPOINT.


