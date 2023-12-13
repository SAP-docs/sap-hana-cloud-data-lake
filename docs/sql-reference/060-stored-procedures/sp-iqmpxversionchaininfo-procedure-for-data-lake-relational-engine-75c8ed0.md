<!-- loio75c8ed076eed41ae914648167432ca1a -->

# sp\_iqmpxversionchaininfo Procedure for Data Lake Relational Engine

Displays detailed status information about the current database.



<a name="loio75c8ed076eed41ae914648167432ca1a__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxversionchaininfo <detailLevel>;
```



<a name="loio75c8ed076eed41ae914648167432ca1a__section_rht_h4c_kkb"/>

## Parameters


<dl>
<dt><b>

*<detailLevel\>*

</b></dt>
<dd>

Enables you to set the level of detail for log messages that are logged to data lake Relational Engine log messages file \(<code><i class="varname">&lt;server_name&gt;</i>.iqmsg</code>\). Allowed values are:

-   0 – All the information is printed on the console and no information is logged to the log file.
-   1 – The list of versions that are being used by each worker node is logged.
-   2 – Information of all transaction control blocks for each worker node are logged, along with the list of versions that are being used by each worker node.



</dd>
</dl>



<a name="loio75c8ed076eed41ae914648167432ca1a__section_fqg_g4g_nbb"/>

## Result Set

****


<table>
<tr>
<th valign="top">

Measurement

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

ServerID

</td>
<td valign="top">

The ID of the worker node.

</td>
</tr>
<tr>
<td valign="top">

CurrentVersion

</td>
<td valign="top">

The latest \(newest\) version this node is aware of.

</td>
</tr>
<tr>
<td valign="top">

LastActiveVersion

</td>
<td valign="top">

The last \(oldest\) version that any transaction on this node refers to.

</td>
</tr>
<tr>
<td valign="top">

OARV

</td>
<td valign="top">

The oldest active reader version across the entire multiplex. This value is the same across all rows.

</td>
</tr>
<tr>
<td valign="top">

LastAppliedVersion

</td>
<td valign="top">

The last \(recent\) version that was applied \(cleaned-up\) on the coordinator node. This value is the same across all rows.

</td>
</tr>
</table>



<a name="loio75c8ed076eed41ae914648167432ca1a__iq_iqmpx_259"/>

## Remarks

sp\_iqmpxversionchaininfo helps investigate version buildup issues in the system by way of locating the node responsible for the buildup.



<a name="loio75c8ed076eed41ae914648167432ca1a__iq_iqmpx_258"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



<a name="loio75c8ed076eed41ae914648167432ca1a__section_hkk_xwh_jkb"/>

## Restrictions

sp\_iqmpxversionchaininfo can only be run on the coordinator node. If you run it on the worker node, it returns the following error:

```
sp_iqmpxversionchaininfo cannot be run on Secondary nodes.
SQLCODE= -1012068, ODBC 3 State="HY000" Line 1, column 1."
```



<a name="loio75c8ed076eed41ae914648167432ca1a__section_utq_cf3_jkb"/>

## Examples

Query:

```
sp_iqmpxversionchaininfo 0;
```

Result:

```

ServerID  CurrentVersion   LastActiveVersion   OARV   LastAppliedVersion
––––––--  –––––––––––––-   ––––––––––––––––-   –––-   ––––––––––––––––--
2         427              427                 427     427
3         427              427                 427     427
4         427              427                 427     427
5         427              427                 427     427
```

