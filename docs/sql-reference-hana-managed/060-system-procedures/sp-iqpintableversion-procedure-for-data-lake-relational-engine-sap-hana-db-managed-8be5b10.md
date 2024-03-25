<!-- loio8be5b10546044be286c45b54dadb9764 -->

# sp\_iqpintableversion Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Pin the committed table version that is visible to the transaction.



<a name="loio8be5b10546044be286c45b54dadb9764__section_n4l_ryb_4zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_iqpintableversion ( '<table-id>[, <table-id>[,...] ]'[, {'<owner-cookie>' | NULL } [, <track-updates> ] ]  )
```



<a name="loio8be5b10546044be286c45b54dadb9764__section_kg5_5yb_4zb"/>

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



<a name="loio8be5b10546044be286c45b54dadb9764__section_rrl_vyb_4zb"/>

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



<a name="loio8be5b10546044be286c45b54dadb9764__section_snp_wyb_4zb"/>

## Remarks

This operation is transactional. A user must commit the transaction to persist the change, if AUTO COMMIT is not enabled. Only committed table versions can be pinned. If the table version visible to the transaction is a non-committed table version, then the store procedure fails with an error. If *<track\_updates\>* is enabled \(set to 1\), then the table version visible to the calling transaction must be the latest committed table version. Otherwise, the procedure fails with an error.



<a name="loio8be5b10546044be286c45b54dadb9764__section_wyq_xyb_4zb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.

Also requires one of the following:

-   SELECT ANY TABLE system privilege
-   SELECT object-level privilege on the tables of the pin request
-   SELECT object-level privilege on the schema containing the object in the relational container.

Also requires one of the following:

-   MANAGE ANY OLD TABLE VERSION system privilege
-   MANAGE OLD TABLE VERSION system privilege



<a name="loio8be5b10546044be286c45b54dadb9764__section_gsh_yyb_4zb"/>

## Example

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

2.  Assuming the table ID for tables C1 and C2 are 1864 and 1865 respectively, pin the current visible version for both tables in a single pin request, To help identify the contents of the pinned request, you could specify an optional name to the request, such as C1-C2. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

    ```
    CALL sp_iqpintableversion('1864,1865','C1-C2');
    COMMIT;
    ```


This example pins the currently visible version of table id 1836, without an optional name, and track updates made to the table. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

```
CALL sp_iqpintableversion('1836', NULL, 1);
COMMIT:
```

