<!-- loio3bdec70a6c5f1014bbc6f1a140c8855d -->

# Cursor Requests in ADO/OLE DB and ODBC

The following table illustrates the cursor sensitivity that is set in response to different ODBC scrollable cursor types.


<table>
<tr>
<th valign="top">

ODBC Scrollable Cursor Type



</th>
<th valign="top">

Cursor Sensitivity



</th>
</tr>
<tr>
<td valign="top">

STATIC



</td>
<td valign="top">

Insensitive



</td>
</tr>
<tr>
<td valign="top">

KEYSET-DRIVEN



</td>
<td valign="top">

Value-sensitive



</td>
</tr>
<tr>
<td valign="top">

DYNAMIC



</td>
<td valign="top">

Sensitive



</td>
</tr>
<tr>
<td valign="top">

MIXED



</td>
<td valign="top">

Value-sensitive



</td>
</tr>
</table>

A MIXED cursor is obtained by setting the cursor type to SQL\_CURSOR\_KEYSET\_DRIVEN, and then specifying the number of rows in the keyset for a keyset-driven cursor using SQL\_ATTR\_KEYSET\_SIZE. If the keyset size is 0 \(the default\), the cursor is fully keyset-driven. If the keyset size is greater than 0, the cursor is mixed \(keyset-driven within the keyset and dynamic outside the keyset\). The default keyset size is 0. It is an error if the keyset size is greater than 0 and less than the rowset size \(SQL\_ATTR\_ROW\_ARRAY\_SIZE\).

ODBC cursor characteristics help you decide the curser type to request.



## Exceptions

If a STATIC cursor is requested as updatable, a value-sensitive cursor is supplied instead and a warning is issued.

If a DYNAMIC or MIXED cursor is requested and the query cannot be executed without using work tables, a warning is issued and an asensitive cursor is supplied instead.

