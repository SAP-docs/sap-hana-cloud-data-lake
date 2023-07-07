<!-- loio3be5cf0d6c5f1014a541be39e0932595 -->

# sa\_get\_user\_status System Procedure for Data Lake Relational Engine

Allows you to determine the current status of users.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_get_user_status( )
```



## Result Set


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

user\_id



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

A unique number identifying the user.



</td>
</tr>
<tr>
<td valign="top">

user\_name



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name of the user.



</td>
</tr>
<tr>
<td valign="top">

connections



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

The current number of connections by this user.



</td>
</tr>
<tr>
<td valign="top">

failed\_logins



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The number of failed login attempts made by the user.



</td>
</tr>
<tr>
<td valign="top">

last\_login\_time



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Returns the database server local date and time \(accurate to hours and minutes\) that the most recent connection was established. This value is affected by simulated time zone.



</td>
</tr>
<tr>
<td valign="top">

locked



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Indicates if the user account is locked.



</td>
</tr>
<tr>
<td valign="top">

reason\_locked



</td>
<td valign="top">

LONG VARCHAR



</td>
<td valign="top">

The reason the account is locked.



</td>
</tr>
<tr>
<td valign="top">

user\_dn



</td>
<td valign="top">

CHAR\(1024\)



</td>
<td valign="top">

The Distinguished Name \(DN\) for a user ID connecting to an LDAP server.



</td>
</tr>
<tr>
<td valign="top">

user\_dn\_cached\_at



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

The date and time that the user\_dn column was last cached. This value is used to determine whether to purge an old DN. Regardless of the database server local time zone, the value is stored in Coordinated Universal Time \(UTC\). This value is not affected by simulated time zone.



</td>
</tr>
<tr>
<td valign="top">

password\_change\_state



</td>
<td valign="top">

BIT



</td>
<td valign="top">

A value that indicates whether a dual password change is in progress \(0=No, 1=Yes\). The default is 0.



</td>
</tr>
<tr>
<td valign="top">

password\_change\_first\_user



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The user\_id of the user who set the first part of a dual password; otherwise NULL.



</td>
</tr>
<tr>
<td valign="top">

password\_change\_second\_user



</td>
<td valign="top">

UNSIGNED INTEGER



</td>
<td valign="top">

The user\_id of the user who set the second part of a dual password; otherwise NULL.



</td>
</tr>
</table>



## Remarks

This procedure returns a result set that shows the current status of users. In addition to basic user information, the procedure includes a column indicating if the user has been locked out and a column with a reason for the lockout. Users can be locked out for the following reasons: locked due to policy, password expiry, or too many failed attempts.

If the user is authenticated using LDAP User Authentication, the output includes the user's distinguished name and the date and time that the distinguished name was found.



## Privileges

Requires EXECUTE object-level privilege on the procedure.

To view information about other users, also requires the MANAGE ANY USER system privilege.



## Side Effects

None



The following example uses the sa\_get\_user\_status system procedure to return the status of database users.

```
CALL sa_get_user_status;
```

