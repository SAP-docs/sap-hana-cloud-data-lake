<!-- loiob840d01e1af14cd490c991e2b6ce6a0d -->

# sp\_iqpinrequestsize Procedure for Data Lake Relational Engine

Returns the mapping of pin requests to the maximum releaseable size in kilobytes.



<a name="loiob840d01e1af14cd490c991e2b6ce6a0d__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqpinrequestsize()
```



<a name="loiob840d01e1af14cd490c991e2b6ce6a0d__pin_request_size_returns1"/>

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



<a name="loiob840d01e1af14cd490c991e2b6ce6a0d__pin_request_size_remarks1"/>

## Remarks

sp\_iqpinrequestsize can only be run on the coordinator node. The coordinator endpoint can be found on the *Action* menu for the instance in SAP HANA Cloud Central.



<a name="loiob840d01e1af14cd490c991e2b6ce6a0d__pin_request_size_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.



<a name="loiob840d01e1af14cd490c991e2b6ce6a0d__pin_request_size_examples1"/>

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

