<!-- loioa44c032384f21015af648b695e72aee9 -->

# sp\_has\_role System Procedure for Data Lake Relational Engine

Returns an integer value indicating whether the invoking user has been granted a specified system privilege or user-defined role. When used for privilege checking within user-defined stored procedures, sp\_has\_role returns an error message when a user fails a privilege check.



```
sp_has_role ( [ <rolename>[, <grant_type>[, <throw_error> ] ] ] )
```



## Parameters


<dl>
<dt><b>

*<rolename\>*

</b></dt>
<dd>

The name of a system privilege or user-defined role.



</dd><dt><b>

*<grant\_type\>*

</b></dt>
<dd>

Valid values are: ADMIN and NO ADMIN. If NULL or not specified, NO ADMIN is used by default.



</dd><dt><b>

*<throw\_error\>*

</b></dt>
<dd>

Valid values are:

-   1 – display error message specified if system privilege or user-defined role is not granted to invoking user.
-   0 – \(default\) do not display error message if specified system privilege or user-defined role is not granted to invoking user.



</dd>
</dl>



## Result Set


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

sp\_has\_role

</td>
<td valign="top">

Indicates whether the invoking \(current\) user has been granted the specified system privilege or role. Valid values are:


<dl>
<dt><b>

1

</b></dt>
<dd>

System privilege or user-defined role is granted to invoking user.



</dd><dt><b>

0 or ***Permission denied: you do not have permission to execute this command/procedure.***

</b></dt>
<dd>

System privilege or user-defined role is not granted to invoking user. The error message replaces the value 0 when the throw\_error argument is set to 1.



</dd><dt><b>

\-1

</b></dt>
<dd>

The system privilege or user-defined role specified does not exist. No error message appears, even if the throw\_error argument is set to 1.



</dd>
</dl>



</td>
</tr>
</table>



## Remarks

If the value of the grant\_type argument is ADMIN, the function checks whether the invoking user has administrative privileges for the system privilege. If the value of the grant\_type argument is NO ADMIN, the function checks whether the invoking user has privileged use of the system privilege or role.

If the grant\_type argument is not specified, NO ADMIN is used by default and output indicates only whether the invoking user has been granted, either directly or indirectly, the specified system privilege or user-defined role.

If the rolename and grant\_type arguments are both NULL and the throw\_error argument is 1, you see an error message. You may find this useful for those stored procedures where an error message appears after certain values are read from the catalog tables rather than after the checking the presence of certain system privileges for the invoking user.

> ### Note:  
> A permission denied error message is returned if the arguments rolename and grant\_type are set to NULL and throw\_error is set to 1, or if all three arguments are set to NULL.



<a name="loioa44c032384f21015af648b695e72aee9__section_pg4_3kz_wxb"/>

## Privileges

Requires EXECUTE object-level privilege on this procedure.



## Examples

All examples are run using the invoking user, in this case USER1.

```
-- Setup for the following example ---
GRANT CREATE ANY PROCEDURE TO USER1 WITH NO ADMIN OPTION;
```

This example returns the value 1, which indicates that USER1 has been granted the CREATE ANY PROCEDURE system privilege:

```
SELECT sp_has_role ('CREATE ANY PROCEDURE');
```


<table>
<tr>
<th valign="top">

sp\_has\_role\('create any procedure'\)

</th>
</tr>
<tr>
<td valign="top">

1

</td>
</tr>
</table>

This example returns the value 0, which indicates that USER1 has not been granted the CREATE ANY OBJECT system privilege with ADMIN option:

```
SELECT sp_has_role ('CREATE ANY PROCEDURE', 'ADMIN');
```


<table>
<tr>
<th valign="top">

sp\_has\_role\('create any procedure','admin'\)

</th>
</tr>
<tr>
<td valign="top">

0

</td>
</tr>
</table>

This example returns the permission denied error message instead of the value 0 because the *<throw\_error\>* value of 1 was included in the statement.

```
SELECT sp_has_role ('CREATE ANY PROCEDURE', 'ADMIN', 1);
```


<table>
<tr>
<td valign="top">

```
Could not execute 'SELECT sp_has_role ('CREATE ANY procedure', 'ADMIN', 1)'
```

```
Error: Permission denied: you do not have the required system privilege(s) or roles(s) to run this procedure.
```



</td>
</tr>
</table>

This example returns the value -1, because role\_a doesn't exist.

```
SELECT sp_has_role ('role_a');
```


<table>
<tr>
<th valign="top">

sp\_has\_role\('role\_a'\)

</th>
</tr>
<tr>
<td valign="top">

\-1

</td>
</tr>
</table>

