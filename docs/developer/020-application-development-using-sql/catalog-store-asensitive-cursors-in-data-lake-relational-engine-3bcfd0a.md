<!-- loio3bcfd0a66c5f1014b5a8b197094ba881 -->

# Catalog Store Asensitive Cursors in Data Lake Relational Engine 

These cursors do not have well-defined sensitivity in their membership, order, or values. The flexibility that is allowed in the sensitivity permits asensitive cursors to be optimized for performance.

Asensitive cursors are used only for read-only cursor types.



## Standards

Asensitive cursors correspond to the ISO/ANSI standard definition of asensitive cursors, and to ODBC cursors with unspecific sensitivity.



## Programming Interfaces


<table>
<tr>
<th valign="top">

Interface



</th>
<th valign="top">

Cursor Type



</th>
</tr>
<tr>
<td valign="top">

ODBC, ADO/OLE DB



</td>
<td valign="top">

Unspecified sensitivity



</td>
</tr>
<tr>
<td valign="top">

Embedded SQL



</td>
<td valign="top">

DYNAMIC SCROLL



</td>
</tr>
</table>



## Description

A request for an asensitive cursor places few restrictions on the methods used to optimize the query and return rows to the application. For these reasons, asensitive cursors provide the best performance. In particular, the optimizer is free to employ any measure of materialization of intermediate results as work tables, and rows can be prefetched by the client.

There are no guarantees about the visibility of changes to base underlying rows. Some changes may be visible, others not. Membership and order may change at each fetch. In particular, updates to base rows may result in only some of the updated columns being reflected in the cursor's result.

Asensitive cursors do not guarantee to return rows that match the query's selection and order. The row membership is fixed at cursor open time, but subsequent changes to the underlying values are reflected in the results.

Asensitive cursors always return rows that matched the customer's WHERE and ORDER BY clauses at the time the cursor membership is established. If column values change after the cursor is opened, rows may be returned that no longer match WHERE and ORDER BY clauses.

