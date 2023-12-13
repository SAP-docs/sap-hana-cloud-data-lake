<!-- loio56581921e7554ed89d87cae3b71e8a30 -->

# sp\_iqunpinrequest Procedure for Data Lake Relational Engine

Unpin the pin request identified by the specified *<pin\_id\>*.



<a name="loio56581921e7554ed89d87cae3b71e8a30__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqunpinrequest(<pin_id>);
```



<a name="loio56581921e7554ed89d87cae3b71e8a30__iqunpinrequest_param1"/>

## Parameters


<dl>
<dt><b>

*<pin\_id\>*

</b></dt>
<dd>

Specifies the pin ID of the pin request to unpin.



</dd>
</dl>



<a name="loio56581921e7554ed89d87cae3b71e8a30__iqunpinrequest_results1"/>

## Result Set

None



<a name="loio56581921e7554ed89d87cae3b71e8a30__iqunpinrequest_remarks1"/>

## Remarks

This operation is transactional. A user must commit the transaction to persist the change, if AUTO COMMIT is not enabled.



<a name="loio56581921e7554ed89d87cae3b71e8a30__iqunpinrequest_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.

Also requires one of the following:

-   You are the creator of the pin request
-   MANAGE ANY OLD TABLE VERSION system privilege



<a name="loio56581921e7554ed89d87cae3b71e8a30__iqunpinrequest_example1"/>

## Example

This example unpins the pinned pin request identified by pin\_id 13668901889. Since the pin request operation is transactional, a COMMIT is required if AUTO COMMIT is disabled.

```
CALL sp_iqunpinrequest(13668901889);
COMMIT;
```

