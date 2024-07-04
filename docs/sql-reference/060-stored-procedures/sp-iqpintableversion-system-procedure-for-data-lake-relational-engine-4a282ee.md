<!-- loio4a282eef340d4aadbd1ededa15ce30ea -->

# sp\_iqpintableversion System Procedure for Data Lake Relational Engine

Pin the committed table version that is visible to the transaction.



<a name="loio4a282eef340d4aadbd1ededa15ce30ea__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqpintableversion ( '<table-id>[, <table-id>[,...] ]'[, {'<owner-cookie>' | NULL } [, <track-updates> ] ]  )
```



<a name="loio4a282eef340d4aadbd1ededa15ce30ea__iqpintableversion_param1"/>

## Parameters


<dl>
<dt><b>

*<table-id\>*

</b></dt>
<dd>

Specifies the table IDs of the base tables being pinned.



</dd><dt><b>

*<owner-cookie\>*

</b></dt>
<dd>

\(Optional\) Specifies a unique, optional name defined by the creator of the pin request as an alternative means to identify the pin request. Cookie names cannot be prefixed with SYSIQ.



</dd><dt><b>

*<track-updates\>*

</b></dt>
<dd>

\(Optional\) Specifies whether changes to values in existing rows in the base table are tracked by the system. Valid values are 0 \(default\) = not tracked, 1 = track updates.



</dd>
</dl>



<a name="loio4a282eef340d4aadbd1ededa15ce30ea__iqpintableversion_results1"/>

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

pin\_id

</td>
<td valign="top">

Displays the ID of the pin request.

</td>
</tr>
</table>



<a name="loio4a282eef340d4aadbd1ededa15ce30ea__iqpintableversion_remarks1"/>

## Remarks

This operation is transactional. A user must commit the transaction to persist the change, if AUTO COMMIT is not enabled. Only committed table versions can be pinned. If the table version visible to the transaction is a non-committed table version, then the store procedure fails with an error. If *<track\_updates\>* is enabled \(set to 1\), then the table version visible to the calling transaction must be the latest committed table version. Otherwise, the procedure fails with an error.



<a name="loio4a282eef340d4aadbd1ededa15ce30ea__iqpintableversion_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.

Also requires one of the following:

-   You own the underlying table
-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the tables of the pin request
-   SELECT object-level privilege on the schema containing the object if the schema is owned by another user.

Also requires one of the following:

-   MANAGE ANY OLD TABLE VERSION system privilege
-   MANAGE OLD TABLE VERSION system privilege



<a name="loio4a282eef340d4aadbd1ededa15ce30ea__iqpintableversion_example1"/>

## Examples

This example looks up the table ID of table A1 and uses the value to pin the current version for table A1.

1.  Determine the table\_id for table A1.

    ```
    SELECT table_id FROM SYSTAB WHERE table_name = 'A1';
    ```

2.  Assume the table\_id for table A1 is 1835. Pin the version of table A1 that is visible to the transaction without specifying an optional name or tracking updates. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

    ```
    CALL sp_iqpintableversion(1835);
    COMMIT;
    ```


This example pins two tables, C1 and C2, in a single request.

1.  Determine the table ID for both C1 and C2.

    ```
    SELECT table_id FROM SYSTAB WHERE table_name = 'C1';
    SELECT table_id FROM SYSTAB WHERE table_name = 'C2';
    ```


    <table>
    <tr>
    <th valign="top">

    table\_id
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    1759
    
    </td>
    </tr>
    </table>
    
2.  Assuming the table ID for tables C1 and C2 are 1864 and 1865 respectively, pin the current visible version for both tables in a single pin request, To help identify the contents of the pinned request, you could specify an optional name to the request, such as C1-C2. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

    ```
    CALL sp_iqpintableversion('1864,1865','C1-C2');
    COMMIT;
    ```


    <table>
    <tr>
    <th valign="top">

    pin\_id
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    1891981313
    
    </td>
    </tr>
    </table>
    

This example pins the currently visible version of table id 1836, without an optional name, and track updates made to the table. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

```
CALL sp_iqpintableversion('1836', NULL, 1);
COMMIT:
```

