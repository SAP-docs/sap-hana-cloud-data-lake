<!-- loio3be6e8886c5f101499f0f49f10ebba92 -->

# SYS.SYSCAPABILITYNAME System View for Data Lake Relational Engine

Each row in the SYS.SYSCAPABILITYNAME system view provides a name for each capability ID in the SYSCAPABILITY system view.



<a name="loio3be6e8886c5f101499f0f49f10ebba92__section_skg_rcq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

capid

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

A number uniquely identifying the capability.

</td>
</tr>
<tr>
<td valign="top">

capname

</td>
<td valign="top">

VARCHAR\(32000\)

</td>
<td valign="top">

The name of the capability.

</td>
</tr>
</table>



## Remarks

The SYS.SYSCAPABILITYNAME system view is defined using a combination of dbo.sa\_rowgenerator and the following server properties:

-   RemoteCapability
-   MaxRemoteCapability

