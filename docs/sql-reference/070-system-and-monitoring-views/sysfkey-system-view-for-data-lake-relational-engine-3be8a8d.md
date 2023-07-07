<!-- loio3be8a8d96c5f1014bb2cb502516a5227 -->

# SYSFKEY System View for Data Lake Relational Engine

Each row in the SYSFKEY system view describes a foreign key constraint in the system. The underlying system table for this view is ISYSFKEY.



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

foreign\_table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The table number of the foreign table.



</td>
</tr>
<tr>
<td valign="top">

foreign\_index\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The index number for the foreign key.



</td>
</tr>
<tr>
<td valign="top">

primary\_table\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The table number of the primary table.



</td>
</tr>
<tr>
<td valign="top">

primary\_index\_id



</td>
<td valign="top">

UNSIGNED INT



</td>
<td valign="top">

The index number of the primary key.



</td>
</tr>
<tr>
<td valign="top">

match\_type



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

The matching type for the constraint. Matching types include:


<dl>
<dt><b>

0

</b></dt>
<dd>

Use the default matching



</dd><dt><b>

1

</b></dt>
<dd>

SIMPLE



</dd><dt><b>

2

</b></dt>
<dd>

FULL



</dd><dt><b>

129

</b></dt>
<dd>

SIMPLE UNIQUE



</dd><dt><b>

130

</b></dt>
<dd>

FULL UNIQUE



</dd>
</dl>

For more information about match types, see the MATCH clause of the CREATE TABLE statement.



</td>
</tr>
<tr>
<td valign="top">

check\_on\_commit



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates whether INSERT and UPDATE statements should wait until the COMMIT to check if foreign keys are still valid. Values are 'Y' for wait or 'N' for do not wait.



</td>
</tr>
<tr>
<td valign="top">

nulls



</td>
<td valign="top">

CHAR\(1\)



</td>
<td valign="top">

Indicates whether the columns in the foreign key are allowed to contain the NULL value. This setting is independent of the nulls setting in the columns contained in the foreign key. Values are 'Y' for allowed or 'N' for not allowed.



</td>
</tr>
</table>

**Related Information**  


[SYSFKEY System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/24f16387665e47a492bd2517a5a27a33.html "Each row in the SYSFKEY system view describes a foreign key constraint in the system. The underlying system table for this view is ISYSFKEY.") :arrow_upper_right:

