<!-- loio817d38646ce2101484b2a89df7e62454 -->

# SYSMUTEXSEMAPHORE System View for Data Lake Relational Engine

Each row in the SYSMUTEXSEMAPHORE system view provides information about a user-defined mutex or semaphore in the database. The underlying system table for this view is ISYSMUTEXSEMAPHORE.



<a name="loio817d38646ce2101484b2a89df7e62454__section_d41_rpq_b4b"/>

## Usage

This data lake Relational Engine system view can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



You must have the SELECT ANY TABLE privilege to access this view.


<table>
<tr>
<th valign="top">

Column

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

mutex\_semaphore\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

A unique ID for the mutex or semaphore.

</td>
</tr>
<tr>
<td valign="top">

object\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The object ID of the mutex or semaphore in the ISYSOBJECT system table.

</td>
</tr>
<tr>
<td valign="top">

owner

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The owner of the mutex or semaphore.

</td>
</tr>
<tr>
<td valign="top">

name

</td>
<td valign="top">

CHAR\(128\)

</td>
<td valign="top">

The name of the mutex or semaphore.

</td>
</tr>
<tr>
<td valign="top">

obj\_type

</td>
<td valign="top">

CHAR\(9\)

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

scope

</td>
<td valign="top">

CHAR\(11\)

</td>
<td valign="top">

The scope for the mutex or semaphore. For mutexes, CONNECTION indicates a connection-level scope, and TRANSACTION indicates a transaction-level scope. For semaphores, this value is always CONNECTION.

</td>
</tr>
<tr>
<td valign="top">

start\_with

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The initial counter value for a semaphore. This value is NULL for mutexes.

</td>
</tr>
</table>

