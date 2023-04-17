<!-- loio3be27d566c5f101492adc7dd04a0c3e9 -->

# Catalog Store Cursor Attributes in Data Lake Relational Engine  

Any cursor, once opened, has an associated result set. The cursor is kept open for a length of time. During that time, the result set associated with the cursor may be changed, either through the cursor itself or, subject to isolation level requirements, by other transactions.

Some cursors permit changes to the underlying data to be visible, while others do not reflect these changes. A sensitivity to changes to the underlying data causes different cursor behavior, or **cursor sensitivity**.

Cursors with a variety of sensitivity characteristics are provided.



## Membership, Order, and Value Changes

Changes to the underlying data can affect the result set of a cursor in the following ways:

Membership
:   The set of rows in the result set, as identified by their primary key values.

Order
:   The order of the rows in the result set.

Value
:   The values of the rows in the result set.

For example, consider the following simple table with employee information \(EmployeeID is the primary key column\):


<table>
<tr>
<th valign="top">

EmployeeID



</th>
<th valign="top">

Surname



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

Whitney



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

Cobb



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

Chin



</td>
</tr>
</table>

A cursor on the following query returns all results from the table in primary key order:

```
SELECT EmployeeID, Surname
FROM Employees
ORDER BY EmployeeID;
```

The membership of the result set could be changed by adding a new row or deleting a row. The values could be changed by changing one of the names in the table. The order could be changed by changing the primary key value of one of the employees.



## Visible and Invisible Changes

Subject to isolation level requirements, the membership, order, and values of the result set of a cursor can be changed after the cursor is opened. Depending on the type of cursor in use, the result set as seen by the application may or may not change to reflect these changes.

Changes to the underlying data may be **visible** or **invisible** through the cursor. A visible change is a change that is reflected in the result set of the cursor. Changes to the underlying data that are not reflected in the result set seen by the cursor are invisible.

