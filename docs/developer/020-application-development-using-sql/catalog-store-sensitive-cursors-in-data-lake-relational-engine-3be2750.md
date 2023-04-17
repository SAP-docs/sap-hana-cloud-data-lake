<!-- loio3be275016c5f10148015f2728abd49eb -->

# Catalog Store Sensitive Cursors in Data Lake Relational Engine 

Sensitive cursors can be used for read-only or updatable cursor types.

These cursors have sensitive membership, order, and values.



## Standards

Sensitive cursors correspond to the ISO/ANSI standard definition of sensitive cursors, and to ODBC dynamic cursors.



## Programming Onterfaces


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

Dynamic



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

Embedded SQL



</td>
<td valign="top">

SENSITIVE



</td>
<td valign="top">

Also supplied in response to a request for a DYNAMIC SCROLL cursor when no work table is required and the prefetch option is set to Off.



</td>
</tr>
<tr>
<td valign="top">

JDBC



</td>
<td valign="top">

SENSITIVE



</td>
<td valign="top">

Sensitive cursors are fully supported by the SAP IQ JDBC driver.



</td>
</tr>
</table>



## Description

Prefetching is disabled for sensitive cursors. All changes are visible through the cursor, including changes through the cursor and from other transactions. Higher isolation levels may hide some changes made in other transactions because of locking.

Changes to cursor membership, order, and all column values are all visible. For example, if a sensitive cursor contains a join, and one of the values of one of the underlying tables is modified, then all result rows composed from that base row show the new value. Result set membership and order may change at each fetch.

Sensitive cursors always return rows that match the query's selection criteria, and are in the order specified by any ORDER BY clause. Updates may affect the membership, order, and values of the result set.

The requirements of sensitive cursors place restrictions on the implementation of sensitive cursors:

-   Rows cannot be prefetched, as changes to the prefetched rows would not be visible through the cursor. This may impact performance.

-   Sensitive cursors must be implemented without any work tables being constructed, as changes to those rows stored as work tables would not be visible through the cursor.

-   The no work table limitation restricts the choice of join method by the optimizer and therefore may impact performance.

-   For some queries, the optimizer is unable to construct a plan that does not include a work table that would make a cursor sensitive.

    Work tables are commonly used for sorting and grouping intermediate results. A work table is not needed for sorting if the rows can be accessed through an index. It is not possible to state exactly which queries employ work tables, but the following queries do employ them:

    -   UNION queries, although UNION ALL queries do not necessarily use work tables.

    -   Statements with an ORDER BY clause, if there is no index on the ORDER BY column.

    -   Any query that is optimized using a hash join.

    -   Many queries involving DISTINCT or GROUP BY clauses.


    In these cases, either an error is returned to the application, or the cursor type is changed to an asensitive cursor and a warning is returned.


