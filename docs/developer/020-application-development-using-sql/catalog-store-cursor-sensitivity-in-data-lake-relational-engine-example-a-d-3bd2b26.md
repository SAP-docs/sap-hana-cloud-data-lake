<!-- loio3bd2b2626c5f1014b552be3c7d5c7a76 -->

# Catalog Store Cursor Sensitivity in Data Lake Relational Engine Example: A Deleted Row

This example uses a simple query to illustrate how different cursors respond to a row in the result set being deleted.



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

4.  A separate transaction deletes employee 102 \(Whitney\) and commits the change.


The results of cursor actions in this situation depend on the cursor sensitivity:

Insensitive cursors
:   The DELETE is not reflected in either the membership or values of the results as seen through the cursor:


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

    Returns `Row Not Found`. There is no previous row.


    
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
    
Value-sensitive cursors
:   The membership of the result set is fixed, and so row 105 is still the second row of the result set. The DELETE is reflected in the values of the cursor, and creates an effective hole in the result set.


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

    Returns `No current row of cursor`. There is a hole in the cursor where the first row used to be.


    
    </td>
    </tr>
    <tr>
    <td valign="top">

    Fetch the first row \(absolute fetch\)


    
    </td>
    <td valign="top">

    Returns `No current row of cursor`. There is a hole in the cursor where the first row used to be.


    
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

    The benefit of asensitive cursors is that for many applications, sensitivity is unimportant. In particular, if you are using a forward-only, read-only cursor, no underlying changes are seen. Also, if you are running at a high isolation level, underlying changes are disallowed.

