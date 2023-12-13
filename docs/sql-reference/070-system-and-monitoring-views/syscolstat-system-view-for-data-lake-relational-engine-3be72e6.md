<!-- loio3be72e6a6c5f1014b7f7cf7c154a1b44 -->

# SYSCOLSTAT System View for Data Lake Relational Engine

The SYSCOLSTAT system view contains the column statistics, including histograms, that are used by the optimizer. The contents of this view are best retrieved using the sa\_get\_histogram stored procedure or the Histogram utility. The underlying system table for this view is ISYSCOLSTAT.



<a name="loio3be72e6a6c5f1014b7f7cf7c154a1b44__section_v1w_qbq_b4b"/>

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

table\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A number that uniquely identifies the table or materialized view to which the column belongs.

</td>
</tr>
<tr>
<td valign="top">

column\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A number that, together with table\_id, uniquely identifies the column.

</td>
</tr>
<tr>
<td valign="top">

format\_id

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

update\_time

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

The local time of the last update of the column statistics.

</td>
</tr>
<tr>
<td valign="top">

density

</td>
<td valign="top">

FLOAT

</td>
<td valign="top">

An estimate of the average selectivity of a single value for the column, not counting the large single value selectivities stored in the row.

</td>
</tr>
<tr>
<td valign="top">

max\_steps

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

actual\_steps

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

step\_values

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

frequencies

</td>
<td valign="top">

LONG BINARY

</td>
<td valign="top">

For system use only.

</td>
</tr>
<tr>
<td valign="top">

update\_time\_utc

</td>
<td valign="top">

TIMESTAMP WITH TIME ZONE

</td>
<td valign="top">

The UTC time of the last update of the column statistics.

</td>
</tr>
</table>

