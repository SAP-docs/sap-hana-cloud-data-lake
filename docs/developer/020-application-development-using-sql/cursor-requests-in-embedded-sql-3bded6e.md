<!-- loio3bded6e36c5f1014809dd05768bcdbc8 -->

# Cursor Requests in Embedded SQL

To request a cursor from an Embedded SQL application, you specify the cursor type on the DECLARE statement. The following table illustrates the cursor sensitivity that is set in response to different requests:


<table>
<tr>
<th valign="top">

Cursor Type



</th>
<th valign="top">

Cursor Sensitivity



</th>
</tr>
<tr>
<td valign="top">

NO SCROLL



</td>
<td valign="top">

Asensitive



</td>
</tr>
<tr>
<td valign="top">

DYNAMIC SCROLL



</td>
<td valign="top">

Asensitive



</td>
</tr>
<tr>
<td valign="top">

SCROLL



</td>
<td valign="top">

Value-sensitive



</td>
</tr>
<tr>
<td valign="top">

INSENSITIVE



</td>
<td valign="top">

Insensitive



</td>
</tr>
<tr>
<td valign="top">

SENSITIVE



</td>
<td valign="top">

Sensitive



</td>
</tr>
</table>



## Exceptions

If a DYNAMIC SCROLL or NO SCROLL cursor is requested as UPDATABLE, then a sensitive or value-sensitive cursor is supplied. It is not guaranteed which of the two is supplied. This uncertainty fits the definition of asensitive behavior.

If an INSENSITIVE cursor is requested as UPDATABLE, then a value-sensitive cursor is supplied.

If a DYNAMIC SCROLL cursor is requested, if the prefetch database option is set to Off, and if the query execution plan involves no work tables, then a sensitive cursor may be supplied. Again, this uncertainty fits the definition of asensitive behavior.

