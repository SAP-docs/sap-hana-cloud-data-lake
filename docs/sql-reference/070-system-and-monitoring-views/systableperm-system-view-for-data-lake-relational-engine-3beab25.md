<!-- loio3beab25c6c5f1014b1f7d85f1fe9e90a -->

# SYSTABLEPERM System View for Data Lake Relational Engine

Privileges on tables and views are stored in the SYS.SYSTABLEPERM system view. Each row in this view corresponds to one table, one user ID granting the privilege \(grantor\) and one user ID granted the privilege \(grantee\).



<a name="loio3beab25c6c5f1014b1f7d85f1fe9e90a__section_bg3_c2q_b4b"/>

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

stable\_id

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The table number of the table or view to which the privileges apply.

</td>
</tr>
<tr>
<td valign="top">

grantee

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number of the user ID receiving the privilege.

</td>
</tr>
<tr>
<td valign="top">

grantor

</td>
<td valign="top">

UNSIGNED INT

</td>
<td valign="top">

The user number of the user ID granting the privilege.

</td>
</tr>
<tr>
<td valign="top">

selectauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the SELECT privilege.

-   Y - Grantee can SELECT but cannot re-grant the privilege.
-   G - Grantee can SELECT and can re-grant the privilege.
-   N - Grantee can neither SELECT nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

insertauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the INSERT privilege.

-   Y - Grantee can INSERT but cannot re-grant the privilege.
-   G - Grantee can INSERT and can re-grant the privilege.
-   N - Grantee can neither INSERT nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

deleteauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the DELETE privilege.

-   Y - Grantee can DELETE but cannot re-grant the privilege.
-   G - Grantee can DELETE and can re-grant the privilege.
-   N - Grantee can neither DELETE nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

updateauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the UPDATE privilege.

-   Y - Grantee can UPDATE but cannot re-grant the privilege.
-   G - Grantee can UPDATE and can re-grant the privilege.
-   N - Grantee can neither UPDATE nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

updatecols

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether UPDATE privileges have only been granted for some of the columns in the underlying table. If updatecols has the value Y, there’s one or more rows in the SYS.SYSCOLPERM system view granting update privileges for the columns.

</td>
</tr>
<tr>
<td valign="top">

alterauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the ALTER privilege.

-   Y - Grantee can ALTER but cannot re-grant the privilege.
-   G - Grantee can ALTER and can re-grant the privilege.
-   N - Grantee can neither ALTER nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

referenceauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the RERERENCES privilege.

-   Y - Grantee can RERERENCES but cannot re-grant the privilege.
-   G - Grantee can RERERENCES and can re-grant the privilege.
-   N - Grantee can neither RERERENCES nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

loadauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the LOAD privilege.

-   Y - Grantee can LOAD but cannot re-grant the privilege.
-   G - Grantee can LOAD and can re-grant the privilege.
-   N - Grantee can neither LOAD nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

truncateauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates the grantee's permissions on the TRUNCATE privilege.

-   Y - Grantee can TRUNCATE but cannot re-grant the privilege.
-   G - Grantee can TRUNCATE and can re-grant the privilege.
-   N - Grantee can neither TRUNCATE nor re-grant the privilege.



</td>
</tr>
<tr>
<td valign="top">

backuptableauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether BACKUP TABLE privileges have been granted. Possible values are Y, N, or G. See the following Remarks area for more information about what these values mean.

</td>
</tr>
<tr>
<td valign="top">

restoretableauth

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Indicates whether RESTORE TABLE privileges have been granted. Possible values are Y, N, or G. See the following Remarks area for more information about what these values mean.

</td>
</tr>
</table>



<a name="loio3beab25c6c5f1014b1f7d85f1fe9e90a__SYSTABLEPERM_remarks1"/>

## Remarks

There are several types of privileges that can be granted. Each privilege can have one of the following three values.


<dl>
<dt><b>

N

</b></dt>
<dd>

No, the grantee hasn’t been granted this privilege by the grantor.



</dd><dt><b>

Y

</b></dt>
<dd>

Yes, the grantee has been given this privilege by the grantor.



</dd><dt><b>

G

</b></dt>
<dd>

The grantee has been given this privilege and can grant the same privilege to another user.



</dd>
</dl>



<a name="loio3beab25c6c5f1014b1f7d85f1fe9e90a__SYSTABLEPERM_constraints1"/>

## Constraints on Underlying System Table

```
PRIMARY KEY (stable_id, grantee, grantor);
```

```
FOREIGN KEY (stable_id) REFERENCES SYS.ISYSTAB (table_id);
```

```
FOREIGN KEY (grantor) REFERENCES SYS.ISYSUSER (user_id);
```

```
FOREIGN KEY (grantee) REFERENCES SYS.ISYSUSER (user_id);
```

**Related Information**  


[SYSTABLEPERM System View for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/7808ea6465984320b56b55cebdb45ae1.html "Privileges on tables and views are stored in the SYS.SYSTABLEPERM system view. Each row in this view corresponds to one table, one user ID granting the privilege (grantor) and one user ID granted the privilege (grantee).") :arrow_upper_right:

