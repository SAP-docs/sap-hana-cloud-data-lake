<!-- loio3beac2596c5f101497d5d883cf3766e9 -->

# SYSTEXTIDX System View for Data Lake Relational Engine

Each row in the SYSTEXTIDX system view describes one text index. The underlying system table for this view is ISYSTEXTIDX.



<a name="loio3beac2596c5f101497d5d883cf3766e9__section_bg3_c2q_b4b"/>

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

index\_id

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the text index in SYSIDX.

</td>
</tr>
<tr>
<td valign="top">

sequence

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

status

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

text\_config

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The object ID of the text configuration object in SYSTEXTCONFIG.

</td>
</tr>
<tr>
<td valign="top">

next\_handle

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

last\_handle

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

For internal use only.

</td>
</tr>
<tr>
<td valign="top">

deleted\_length

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The total size of deleted indexed values in the text index.

</td>
</tr>
<tr>
<td valign="top">

pending\_length

</td>
<td valign="top">

UNSIGNED BIGINT

</td>
<td valign="top">

The total size of indexed values that will be added to the text index at the next refresh.

</td>
</tr>
<tr>
<td valign="top">

refresh\_type

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

The type of refresh. One of:


<dl>
<dt><b>

1

</b></dt>
<dd>

MANUAL



</dd><dt><b>

2

</b></dt>
<dd>

AUTO



</dd><dt><b>

3

</b></dt>
<dd>

IMMEDIATE



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

refresh\_interval

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The AUTO REFRESH interval, in minutes.

</td>
</tr>
<tr>
<td valign="top">

last\_refresh

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The local time of the last refresh.

</td>
</tr>
<tr>
<td valign="top">

last\_refresh\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

The UTC time of the last refresh.

</td>
</tr>
</table>

