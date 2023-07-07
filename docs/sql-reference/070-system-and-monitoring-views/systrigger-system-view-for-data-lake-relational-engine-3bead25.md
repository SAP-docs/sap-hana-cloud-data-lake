<!-- loio3bead2516c5f1014980c8a7f234ac01d -->

# SYSTRIGGER System View for Data Lake Relational Engine

Each row in the SYSTRIGGER system view describes one trigger in the database. This view also contains triggers that are automatically created for foreign key definitions which have a referential triggered action \(such as ON DELETE CASCADE\). The underlying system table for this view is ISYSTRIGGER.



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

trigger\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

A unique number for the trigger in the SYSTRIGGER view.



</td>
</tr>
<tr>
<td valign="top">

table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The table ID of the table to which this trigger belongs.



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

The object ID for the trigger in the database.



</td>
</tr>
<tr>
<td valign="top">

event



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

The operation that causes the trigger to fire.


<dl>
<dt><b>

A

</b></dt>
<dd>

INSERT, DELETE



</dd><dt><b>

B

</b></dt>
<dd>

INSERT, UPDATE



</dd><dt><b>

C

</b></dt>
<dd>

UPDATE COLUMNS



</dd><dt><b>

D

</b></dt>
<dd>

DELETE



</dd><dt><b>

E

</b></dt>
<dd>

DELETE, UPDATE



</dd><dt><b>

I

</b></dt>
<dd>

INSERT



</dd><dt><b>

M

</b></dt>
<dd>

INSERT, DELETE, UPDATE



</dd><dt><b>

U

</b></dt>
<dd>

UPDATE



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

trigger\_time



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

The time when the trigger fires relative to the event.


<dl>
<dt><b>

A

</b></dt>
<dd>

AFTER \(row-level trigger\)



</dd><dt><b>

B

</b></dt>
<dd>

BEFORE \(row-level trigger\)



</dd><dt><b>

I

</b></dt>
<dd>

INSTEAD OF \(row-level trigger\)



</dd><dt><b>

K

</b></dt>
<dd>

INSTEAD OF \(statement-level trigger\)



</dd><dt><b>

R

</b></dt>
<dd>

RESOLVE



</dd><dt><b>

S

</b></dt>
<dd>

AFTER \(statement-level trigger\)



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

trigger\_order



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

The order in which are fired when there are multiple triggers of the same type \(insert, update, or delete\) set to fire at the same time \(applies to BEFORE or AFTER triggers only, only\).



</td>
</tr>
<tr>
<td valign="top">

foreign\_table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The ID of the table containing a foreign key definition that has a referential triggered action \(such as ON DELETE CASCADE\). The foreign\_table\_id value reflects the value of ISYSIDX.table\_id.



</td>
</tr>
<tr>
<td valign="top">

foreign\_key\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The ID of the foreign key for the table referenced by foreign\_table\_id. The foreign\_key\_id value reflects the value of ISYSIDX.index\_id.



</td>
</tr>
<tr>
<td valign="top">

referential\_action



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

The action defined by a foreign key. This single-character value corresponds to the action that was specified when the foreign key was created.


<dl>
<dt><b>

C

</b></dt>
<dd>

CASCADE



</dd><dt><b>

D

</b></dt>
<dd>

SET DEFAULT



</dd><dt><b>

N

</b></dt>
<dd>

SET NULL



</dd><dt><b>

R

</b></dt>
<dd>

RESTRICT



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

trigger\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the trigger. One table cannot have two triggers with the same name.



</td>
</tr>
<tr>
<td valign="top">

trigger\_defn



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The command that was used to create the trigger.



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

Remarks about the trigger. This value is stored in the ISYSREMARK system table.



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

The SQL source for the trigger. This value is stored in the ISYSSOURCE system table.



</td>
</tr>
</table>

