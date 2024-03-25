<!-- loiocd2fbc63744f47b28252976bc905b684 -->

# sp\_iqpinrequestsize Procedure in Data Lake Relational Engine \(SAP HANA DB-Managed\)

Returns the mapping of pin requests to the maximum releaseable size in kilobytes.



<a name="loiocd2fbc63744f47b28252976bc905b684__section_ldn_m2w_qzb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE\_DDL procedure.



```
sp_iqpinrequestsize()
```



<a name="loiocd2fbc63744f47b28252976bc905b684__section_w2g_zdb_hwb"/>

## Result Set

Returns the mapping of pin requests to the maximum releaseable size in kilobytes.


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
<tr>
<td valign="top">

max\_kb\_release

</td>
<td valign="top">

Displays the maximum size, in kilobytes, to be released if the pin request is deleted.

</td>
</tr>
</table>



<a name="loiocd2fbc63744f47b28252976bc905b684__section_v5t_zdb_hwb"/>

## Remarks

sp\_iqpinrequestsize can only be run on the coordinator node. The coordinator endpoint can be found on the *Action* menu for the instance in SAP HANA Cloud Central.



<a name="loiocd2fbc63744f47b28252976bc905b684__section_tch_jv1_1yb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loiocd2fbc63744f47b28252976bc905b684__section_zkm_mfw_qzb"/>

## Examples

This example returns the size each pin request found.

```
CALL sp_iqpinrequestsize();
```


<table>
<tr>
<th valign="top">

pin\_id

</th>
<th valign="top">

max\_kb\_release

</th>
</tr>
<tr>
<td valign="top">

14140968961

</td>
<td valign="top">

1216

</td>
</tr>
<tr>
<td valign="top">

14141034497

</td>
<td valign="top">

1216

</td>
</tr>
<tr>
<td valign="top">

14141037569

</td>
<td valign="top">

1216

</td>
</tr>
</table>

