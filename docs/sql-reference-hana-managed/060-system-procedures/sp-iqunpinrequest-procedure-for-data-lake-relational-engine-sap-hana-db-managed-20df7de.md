<!-- loio20df7deea32f435391aa22218adb95e4 -->

# sp\_iqunpinrequest Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Unpin the pin request identified by the specified *<pin\_id\>*.



<a name="loio20df7deea32f435391aa22218adb95e4__section_bqg_5xb_4zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_iqunpinrequest(<pin_id>)
```



<a name="loio20df7deea32f435391aa22218adb95e4__section_wss_yxb_4zb"/>

## Parameters


<dl>
<dt><b>

*<pin\_id\>*

</b></dt>
<dd>

Specifies the pin ID of the pin request to unpin.



</dd>
</dl>



<a name="loio20df7deea32f435391aa22218adb95e4__section_il3_zxb_4zb"/>

## Result Set

None



<a name="loio20df7deea32f435391aa22218adb95e4__section_gw2_byb_4zb"/>

## Remarks

This operation is transactional. A user must commit the transaction to persist the change, if AUTO COMMIT is not enabled.



<a name="loio20df7deea32f435391aa22218adb95e4__section_ymf_dyb_4zb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.

Also requires one of the following:

-   You are the creator of the pin request
-   MANAGE ANY OLD TABLE VERSION system privilege



<a name="loio20df7deea32f435391aa22218adb95e4__section_i3m_gyb_4zb"/>

## Example

This example unpins the pinned pin request identified by pin\_id 13668901889. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

```
CALL sp_iqunpinrequest(13668901889);
COMMIT;
```

