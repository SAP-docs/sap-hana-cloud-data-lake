<!-- loioa4db556c84f21015a798ecee7db8720b -->

# sp\_iqmpxversioninfo Procedure for Data Lake Relational Engine

Shows the current version information for this node, including type and synchronization status.



<a name="loioa4db556c84f21015a798ecee7db8720b__section_umy_gqn_14b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sp_iqmpxversioninfo
```



## Result Set


<table>
<tr>
<th valign="top">

Column

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CatalogID

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Catalog version on this node.

</td>
</tr>
<tr>
<td valign="top">

VersionID

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Latest version available on this node.

</td>
</tr>
<tr>
<td valign="top">

OAVID

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Oldest active version on this node.

</td>
</tr>
<tr>
<td valign="top">

ServerType

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Type of node:

-   "C" – Coordinator
-   "W" – Write Server
-   "Q" – Query Server



</td>
</tr>
<tr>
<td valign="top">

CatalogSync

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Catalog synchronization:

-   "T" – synchronized
-   "F" – not synchronized



</td>
</tr>
<tr>
<td valign="top">

WCatalogID

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Catalog version on the write node.

</td>
</tr>
<tr>
<td valign="top">

WVersionID

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

Latest version available on the write node.

</td>
</tr>
</table>



<a name="loioa4db556c84f21015a798ecee7db8720b__iq_iqmpx_261"/>

## Privileges

Requires EXECUTE object-level privilege on the procedure.



## Side Effects

None

