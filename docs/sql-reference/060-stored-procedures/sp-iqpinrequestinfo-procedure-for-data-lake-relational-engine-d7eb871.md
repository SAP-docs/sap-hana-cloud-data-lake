<!-- loiod7eb871b0ea94bc9a20dc8a35a7d08c7 -->

# sp\_iqpinrequestinfo Procedure for Data Lake Relational Engine

Displays information for all persisted pin requests including those that have been unpinned and waiting to be deleted when nobody uses it.



<a name="loiod7eb871b0ea94bc9a20dc8a35a7d08c7__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqpinrequestinfo()
```



<a name="loiod7eb871b0ea94bc9a20dc8a35a7d08c7__iqpinrequestinfo_param1"/>

## Parameters

None



<a name="loiod7eb871b0ea94bc9a20dc8a35a7d08c7__iqpinrequestinfo_results1"/>

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

Specifies the ID of the pin request.

</td>
</tr>
<tr>
<td valign="top">

owner\_cookie

</td>
<td valign="top">

Specifies the user assigned ID of the pin request.

</td>
</tr>
<tr>
<td valign="top">

pinned\_cid

</td>
<td valign="top">

Specifies the commit ID of the transaction whose control block is required to retain the pin request.

</td>
</tr>
<tr>
<td valign="top">

orig\_pinned\_cid

</td>
<td valign="top">

Specifies the commit ID of the original transaction whose control block is required to retain the pin request.

</td>
</tr>
<tr>
<td valign="top">

txn\_id

</td>
<td valign="top">

Specifies the transaction ID of the pinning transaction.

</td>
</tr>
<tr>
<td valign="top">

commit\_id

</td>
<td valign="top">

Specifies the commit ID of the pinning transaction.

</td>
</tr>
<tr>
<td valign="top">

unpinned\_at

</td>
<td valign="top">

Specifies the commit ID of the unpinning transaction. A non-zero value indicates the pin request has been unpinned, is not accessible, and is waiting to be deleted by the system.

</td>
</tr>
<tr>
<td valign="top">

ref\_count

</td>
<td valign="top">

Specifies how many connections are currently using this pin request on the server where sp\_iqpinrequestinfo\(\) is being executed.

</td>
</tr>
<tr>
<td valign="top">

pin\_time

</td>
<td valign="top">

Specifies the timestamp when the pin request was committed.

</td>
</tr>
<tr>
<td valign="top">

frozen\_time

</td>
<td valign="top">

Specifies the time that data lake Relational Engine determines the *<pinned\_cid\>*.

</td>
</tr>
<tr>
<td valign="top">

num\_tables

</td>
<td valign="top">

Specifies the number of tables pinned by the pin request.

</td>
</tr>
<tr>
<td valign="top">

frozen

</td>
<td valign="top">

For Internal use only.

</td>
</tr>
<tr>
<td valign="top">

track\_updates

</td>
<td valign="top">

Specifies if data lake Relational Engine tracks the updates made since the pin request was committed. Valid values are T\(rue\) and F\(alse\).

</td>
</tr>
<tr>
<td valign="top">

obsolete

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

servers

</td>
<td valign="top">

Specifies a comma separated list of IDs of the secondary servers currently using the pin request.

</td>
</tr>
</table>



<a name="loiod7eb871b0ea94bc9a20dc8a35a7d08c7__iqpinrequestinfo_remarks1"/>

## Remarks

None



<a name="loiod7eb871b0ea94bc9a20dc8a35a7d08c7__iqpinrequestinfo_priv1"/>

## Privileges



### 

Requires EXECUTE object-level privilege on the procedure.

**Related Information**  


[sp_iqpinrequestinfo Procedure for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_1_QRC/en-US/bb623feb1ed64078904a91ea30f70d98.html "Displays information for all persisted pin requests including those that have been unpinned and waiting to be deleted when nobody uses it.") :arrow_upper_right:

