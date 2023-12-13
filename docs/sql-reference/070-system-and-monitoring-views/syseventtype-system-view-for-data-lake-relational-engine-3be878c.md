<!-- loio3be878c46c5f101487258bb0580a6afa -->

# SYSEVENTTYPE System View for Data Lake Relational Engine

The SYSEVENTTYPE system view defines the system event types that can be referenced by CREATE EVENT.



<a name="loio3be878c46c5f101487258bb0580a6afa__section_v1w_qbq_b4b"/>

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

event\_type\_id

</td>
<td valign="top">

INT

</td>
<td valign="top">

The unique number assigned to each event type.

</td>
</tr>
<tr>
<td valign="top">

name

</td>
<td valign="top">

VARCHAR\(32000\)

</td>
<td valign="top">

The name of the system event type.

</td>
</tr>
<tr>
<td valign="top">

description

</td>
<td valign="top">

VARCHAR\(32000\)

</td>
<td valign="top">

A description of the system event type.

</td>
</tr>
</table>



<a name="loio3be878c46c5f101487258bb0580a6afa__syseventtype_remarks1"/>

## Remarks

The SYSEVENTTYPE system view is defined using a combination of sa\_rowgenerator and the following server properties:

-   EventTypeName
-   EventTypeDesc
-   MaxEventType

