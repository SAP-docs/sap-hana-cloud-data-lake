<!-- loio3be86e856c5f10149f4ed7d9e5f2c454 -->

# SYSEVENT System View for Data Lake Relational Engine

Each row in the SYSEVENT system view describes an event created with CREATE EVENT. The underlying system table for this view is ISYSEVENT.



> ### Restriction:  
> This data lake Relational Engine system view can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




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

event\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The unique number assigned to each event.



</td>
</tr>
<tr>
<td valign="top">

object\_id



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

The internal ID for the event, uniquely identifying it in the database.



</td>
</tr>
<tr>
<td valign="top">

creator



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The user number of the owner of the event. The name of the user can be found by looking in the SYSUSER system view.



</td>
</tr>
<tr>
<td valign="top">

event\_name



</td>
<td valign="top">

VARCHAR\(128\)



</td>
<td valign="top">

The name of the event.



</td>
</tr>
<tr>
<td valign="top">

enabled



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates whether the event is allowed to fire.



</td>
</tr>
<tr>
<td valign="top">

location



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

The location where the event is to fire:

-   Y = AT ALL clause and FOR PRIMARY clause specified
-   E = AT CONSOLIDATED clause and FOR PRIMARY clause specified
-   T = AT REMOTE clause and FOR PRIMARY clause specified
-   P = \(AT clause not specified\) FOR PRIMARY clause specified
-   B = AT ALL clause and FOR ALL clause specified
-   D = AT CONSOLIDATED clause and FOR ALL clause specified
-   S = AT REMOTE clause and FOR ALL clause specified
-   M = \(AT clause not specified\) FOR ALL clause specified
-   C = AT CONSOLIDATED \(FOR clause not specified\)
-   R = AT REMOTE \(FOR clause not specified\)
-   A = AT ALL clause \(FOR clause not specified\)



</td>
</tr>
<tr>
<td valign="top">

event\_type\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

For system events, the event type as listed in the SYSEVENTTYPE system view.



</td>
</tr>
<tr>
<td valign="top">

action



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The event handler definition. An obfuscated value indicates a hidden event.



</td>
</tr>
<tr>
<td valign="top">

external\_action



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

For system use only.



</td>
</tr>
<tr>
<td valign="top">

condition



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The condition used to control firing of the event handler.



</td>
</tr>
<tr>
<td valign="top">

remarks



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

Remarks for the event; this column comes from ISYSREMARK.



</td>
</tr>
<tr>
<td valign="top">

source



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The original source for the event; this column comes from ISYSSOURCE.



</td>
</tr>
</table>

