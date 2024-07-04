<!-- loioa4db1be484f21015bfe3fc26275f8447 -->

# sp\_iqmpxvalidate System Procedure for Data Lake Relational Engine

Checks the multiplex cluster configuration for inconsistencies.



<a name="loioa4db1be484f21015bfe3fc26275f8447__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxvalidate()
```



<a name="loioa4db1be484f21015bfe3fc26275f8447__section_lm4_ppc_fbc"/>

## Parameters

None.



<a name="loioa4db1be484f21015bfe3fc26275f8447__section_fqg_g4g_nbb"/>

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

Messages

</td>
<td valign="top">

Displays an error message for the severity level.

</td>
</tr>
<tr>
<td valign="top">

Severity

</td>
<td valign="top">

Displays the severity level number.

</td>
</tr>
</table>



<a name="loioa4db1be484f21015bfe3fc26275f8447__iq_iqmpx_259"/>

## Remarks

Returns a severity result to the caller. Values are:

-   0 – No errors detected
-   1 – Dynamic state isn't as expected.
-   2 – Nonfatal configuration error; for example, multiplex operation impaired.
-   3 – Fatal configuration problem; for example, one or more nodes doesn't start.

Executes multiple checks on tables `SYS.SYSIQDBFILE` and other multiplex events and stored procedures. May run on any node.

Returns rows listing all errors and their severity. If called interactively, with the optional calling parameter 'N', then returns only the severity status.

Each error indicates its severity. If there are no errors, the procedure returns `No errors detected`.



<a name="loioa4db1be484f21015bfe3fc26275f8447__iq_iqmpx_258"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Side Effects

None.



<a name="loioa4db1be484f21015bfe3fc26275f8447__section_glm_stc_fbc"/>

## Examples

This example checks the multiplex cluster for inconsistencies.

```
CALL  sp_iqmpxvalidate;
```


<table>
<tr>
<th valign="top">

Messages

</th>
<th valign="top">

Severity

</th>
</tr>
<tr>
<td valign="top">

WARNING: Server mpx-writer-0-0 has no Temp dbspaces

</td>
<td valign="top">

2

</td>
</tr>
</table>

