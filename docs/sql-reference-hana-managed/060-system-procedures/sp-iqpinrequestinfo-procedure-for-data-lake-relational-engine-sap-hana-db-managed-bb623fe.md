<!-- loiobb623feb1ed64078904a91ea30f70d98 -->

# sp\_iqpinrequestinfo Procedure for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Displays information for all persisted pin requests including those that have been unpinned and waiting to be deleted when nobody uses it.



<a name="loiobb623feb1ed64078904a91ea30f70d98__section_nyf_4xb_4zb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) system procedure can be used when:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.

> ### Restriction:  
> This syntax cannot be run when connected to SAP HANA database as a SAP HANA database user and using SAP HANA database REMOTE\_EXECUTE or REMOTE\_EXECUTE\_QUERY.



```
sp_iqpinrequestinfo()
```



<a name="loiobb623feb1ed64078904a91ea30f70d98__section_i1n_pxb_4zb"/>

## Parameters

None.



<a name="loiobb623feb1ed64078904a91ea30f70d98__section_h51_qxb_4zb"/>

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



<a name="loiobb623feb1ed64078904a91ea30f70d98__section_wmt_qxb_4zb"/>

## Remarks

None



<a name="loiobb623feb1ed64078904a91ea30f70d98__section_hz3_sxb_4zb"/>

## Privileges



### 

Requires EXECUTE object-level privilege on this procedure.



<a name="loiobb623feb1ed64078904a91ea30f70d98__section_xby_lyc_fbc"/>

## Examples

This example returns information about current pin requests.

```
CALL sp_iqpinrequestinfo();
```


<table>
<tr>
<th valign="top">

pin\_id

</th>
<th valign="top">

creator

</th>
<th valign="top">

owner\_

cookie

</th>
<th valign="top">

pinned\_

cid

</th>
<th valign="top">

orig\_

pinned\_cid

</th>
<th valign="top">

txn\_id

</th>
<th valign="top">

commit\_id

</th>
<th valign="top">

unpinned\_

at

</th>
<th valign="top">

ref\_

count

</th>
<th valign="top">

pin

\_time

</th>
<th valign="top">

frozen\_

time

</th>
<th valign="top">

num\_

tables

</th>
<th valign="top">

frozen

</th>
<th valign="top">

track

\_updates

</th>
<th valign="top">

obsolete

</th>
<th valign="top">

servers

</th>
</tr>
<tr>
<td valign="top">

1355750401

</td>
<td valign="top">

103

</td>
<td valign="top">

 

</td>
<td valign="top">

0

</td>
<td valign="top">

1323853

</td>
<td valign="top">

1323975

</td>
<td valign="top">

1323980

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

38:30.0

</td>
<td valign="top">

 

</td>
<td valign="top">

1

</td>
<td valign="top">

F

</td>
<td valign="top">

F

</td>
<td valign="top">

F

</td>
<td valign="top">

 

</td>
</tr>
</table>

**Related Information**  


[sp_iqpinrequestinfo System Procedure for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/d7eb871b0ea94bc9a20dc8a35a7d08c7.html "Displays information for all persisted pin requests including those that have been unpinned and waiting to be deleted when nobody uses it.") :arrow_upper_right:

