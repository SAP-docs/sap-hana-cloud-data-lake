<!-- loio3bdeae836c5f10149a2fdff345ef8205 -->

# Catalog Store Cursor Sensitivity in Data Lake Relational Engine Example: An Updated Row

This example uses a simple query to illustrate how different cursor types respond to a row in the result set being updated in such a way that the order of the result set is changed.



Consider the following sequence of events:

1.  An application opens a cursor on the following query against the sample database.

    ```
    SELECT EmployeeID, Surname
    FROM Employees
    ORDER BY EmployeeID;
    ```


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

    102


    
    </td>
    <td valign="top">

    Whitney


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    105


    
    </td>
    <td valign="top">

    Cobb


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    129


    
    </td>
    <td valign="top">

    Chin


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    ...


    
    </td>
    <td valign="top">

    ...


    
    </td>
    </tr>
    </table>
    
2.  The application fetches the first row through the cursor \(102\).

3.  The application fetches the next row through the cursor \(105\).

4.  A separate transaction updates the employee ID of employee 102 \(Whitney\) to 165 and commits the change.


The results of the cursor actions in this situation depend on the cursor sensitivity:

 Insensitive cursors
 :   The UPDATE is not reflected in either the membership or values of the results as seen through the cursor:


    <table>
    <tr>
    <th valign="top">

    Action


    
    </th>
    <th valign="top">

    Result


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Fetch previous row


    
    </td>
    <td valign="top">

    Returns the original copy of the row \(102\).


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the first row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns the original copy of the row \(102\).


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the second row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns the unchanged row \(105\).


    
    </td>
    </tr>
    </table>
    
  Sensitive cursors
 :   The membership of the result set has changed so that row 105 is now the first row in the result set:


    <table>
    <tr>
    <th valign="top">

    Action


    
    </th>
    <th valign="top">

    Result


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Fetch previous row


    
    </td>
    <td valign="top">

    Returns SQLCODE 100. The membership of the result set has changed so that 105 is now the first row. The cursor is moved to the position before the first row.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the first row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns row 105.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the second row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns row 129.


    
    </td>
    </tr>
    </table>
    
    In addition, a fetch on a sensitive cursor returns a SQLE\_ROW\_UPDATED\_WARNING warning if the row has changed since the last reading. The warning is given only once. Subsequent fetches of the same row do not produce the warning.

    Similarly, a positioned update or delete through the cursor on a row since it was last fetched returns the SQLE\_ROW\_UPDATED\_SINCE\_READ error. An application must fetch the row again for an update or delete on a sensitive cursor to work.

    An update to any column causes the warning/error, even if the column is not referenced by the cursor. For example, a cursor on a query returning Surname would report the update even if only the Salary column was modified.

  Value-sensitive cursors
 :   The membership of the result set is fixed, and so row 105 is still the second row of the result set. The UPDATE is reflected in the values of the cursor, and creates an effective "hole" in the result set.


    <table>
    <tr>
    <th valign="top">

    Action


    
    </th>
    <th valign="top">

    Result


    
    </th>
    </tr>
    <tr>
    <td valign="top">

    Fetch previous row


    
    </td>
    <td valign="top">

    Returns SQLCODE 100. The membership of the result set has changed so that 105 is now the first row: The cursor is positioned on the hole: it is before row 105.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the first row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns SQLCODE -197. The membership of the result set has changed so that 105 is now the first row: The cursor is positioned on the hole: it is before row 105.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the second row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns row 105.


    
    </td>
    </tr>
    </table>
    
  Asensitive cursors
 :   For changes, the membership and values of the result set are indeterminate. The response to a fetch of the previous row, the first row, or the second row depends on the particular optimization method for the query, whether that method involved the formation of a work table, and whether the row being fetched was prefetched from the client.

 > ### Note:  
> Update warning and error conditions do not occur in bulk operations mode \(-b database server option\).

