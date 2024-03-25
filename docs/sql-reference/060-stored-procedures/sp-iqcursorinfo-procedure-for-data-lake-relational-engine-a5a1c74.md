<!-- loioa5a1c74e84f21015bdc9be59b4d91a1f -->

# sp\_iqcursorinfo Procedure for Data Lake Relational Engine

Displays detailed information about cursors currently open on the server.



<a name="loioa5a1c74e84f21015bdc9be59b4d91a1f__section_blk_cwh_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqcursorinfo [ <cursor-name> ] [, <conn-handle> ]
```



<a name="loioa5a1c74e84f21015bdc9be59b4d91a1f__iq_refbb_1485"/>

## Parameters


<dl>
<dt><b>

*<cursor-name\>*

</b></dt>
<dd>

The name of the cursor. If only this parameter is specified, sp\_iqcursorinfo returns information about all cursors that have the specified name in all connections.



</dd><dt><b>

*<conn-handle\>*

</b></dt>
<dd>

An integer representing the connection ID. If only this parameter is specified, sp\_iqcursorinfo returns information about all cursors in the specified connection.



</dd>
</dl>



<a name="loioa5a1c74e84f21015bdc9be59b4d91a1f__section_hdj_hsz_mbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Name

</td>
<td valign="top">

The name of the cursor.

</td>
</tr>
<tr>
<td valign="top">

ConnHandle

</td>
<td valign="top">

The ID number of the connection.

</td>
</tr>
<tr>
<td valign="top">

IsUpd

</td>
<td valign="top">

Y: the cursor is updatable; N otherwise.

</td>
</tr>
<tr>
<td valign="top">

IsHold

</td>
<td valign="top">

Y: the cursor is a hold cursor; N otherwise.

</td>
</tr>
<tr>
<td valign="top">

IQConnID

</td>
<td valign="top">

The 10-digit connection ID displayed as part of all messages in the `.iqmsg` file. This number is a monotonically increasing integer that is unique within a server session.

</td>
</tr>
<tr>
<td valign="top">

UserID

</td>
<td valign="top">

User ID \(or user name\) for the user who created and ran the cursor.

</td>
</tr>
<tr>
<td valign="top">

CreateTime

</td>
<td valign="top">

The time of cursor creation.

</td>
</tr>
<tr>
<td valign="top">

CurrentRow

</td>
<td valign="top">

The current position of the cursor in the result set.

</td>
</tr>
<tr>
<td valign="top">

NumFetch

</td>
<td valign="top">

The number of times the cursor fetches a row. The same row can be fetched more than once.

</td>
</tr>
<tr>
<td valign="top">

NumUpdate

</td>
<td valign="top">

The number of times the cursor updates a row, if the cursor is updatable. The same row can be updated more than once.

</td>
</tr>
<tr>
<td valign="top">

NumDelete

</td>
<td valign="top">

The number of times the cursor deletes a row, if the cursor is updatable.

</td>
</tr>
<tr>
<td valign="top">

NumInsert

</td>
<td valign="top">

The number of times the cursor inserts a row, if the cursor is updatable.

</td>
</tr>
<tr>
<td valign="top">

RWTabOwner

</td>
<td valign="top">

The owner of the table that is opened in RW mode by the cursor.

</td>
</tr>
<tr>
<td valign="top">

RWTabName

</td>
<td valign="top">

The name of the table that is opened in RW mode by the cursor.

</td>
</tr>
<tr>
<td valign="top">

CmdLine

</td>
<td valign="top">

The first 4096 characters of the command the user executed.

</td>
</tr>
</table>



<a name="loioa5a1c74e84f21015bdc9be59b4d91a1f__section_dm4_3sz_mbb"/>

## Remarks

The sp\_iqcursorinfo procedure can be invoked without any parameters. If no parameters are specified, sp\_iqcursorinfo returns information about all cursors currently open on the server. If both parameters are specified, sp\_iqcursorinfo reports information about all of the cursors that have the specified name and are in the specified connection.

If you do not specify the first parameter, but specify the second parameter, you must substitute NULL for the omitted parameter. For example, sp\_iqcursorinfo NULL, 1.

The sp\_iqcursorinfo stored procedure displays detailed information about cursors currently open on the server. The sp\_iqcursorinfo procedure enables database administrators to monitor cursor status using just one stored procedure and view statistics such as how many rows have been updated, deleted, and inserted.

If you specify one or more parameters, the result is filtered by the specified parameters. For example, if *<cursor-name\>* is specified, only information about the specified cursor is displayed. If *<conn-handle\>* is specified, sp\_iqcursorinfo returns information only about cursors in the specified connection. If no parameters are specified, sp\_iqcursorinfo displays information about all cursors currently open on the server.



<a name="loioa5a1c74e84f21015bdc9be59b4d91a1f__iq_refbb_1484"/>

## Privileges

Requires all of:

-   EXECUTE object-level privilege on the procedure
-   MONITOR system privilege



## Side Effects

None



<a name="loioa5a1c74e84f21015bdc9be59b4d91a1f__iq_refbb_1491"/>

## Examples

-   The following example displays information about all cursors currently open on the server:

    ```
    sp_iqcursorinfo
    
    Name      ConnHandle      IsUpd      IsHold      IQConnID      UserID
    --------------------------------------------------------------------------
    crsr1              1          Y           N           118         HDLADMIN
    crsr2              3          N           N           118         HDLADMIN
    
    CreateTime               CurrentRow      NumFetch      NumUpdate
    ----------------------------------------------------------------
    2009-06-26 15:24:36.000          19      100000000     200000000
    2009-06-26 15:38:38.000       20000      200000000
    
    NumDelete     NumInsert      RWTabOwner      RWTabName        CmdLine
    ----------------------------------------------------------------------
     20000000    3000000000        HDLADMIN          test1    call proc1()
                                                              call proc2()
    ```

-   The following example displays information about all cursors currently open on the server:

    ```
    sp_iqcursorinfo;
    ```

-   The following example displays information about the all cursors named `cursor1` in all connections:

    ```
    sp_iqcursorinfo 'cursor1';
    ```

-   The following example displays information about all cursors in connection 3:

    ```
    sp_iqcursorinfo NULL, 3;
    ```

-   The following example displays information about all the cursors named `cursor2` in connection 4:

    ```
    sp_iqcursorinfo 'cursor2', 4;
    ```


