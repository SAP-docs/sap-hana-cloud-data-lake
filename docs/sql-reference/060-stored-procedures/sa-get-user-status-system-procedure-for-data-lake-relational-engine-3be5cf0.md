<!-- loio3be5cf0d6c5f1014a541be39e0932595 -->

# sa\_get\_user\_status System Procedure for Data Lake Relational Engine

Allows you to determine the current status of users.



<a name="loio3be5cf0d6c5f1014a541be39e0932595__section_idn_b13_b4b"/>

## Usage

This data lake Relational Engine procedure can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_get_user_status( );
```



<a name="loio3be5cf0d6c5f1014a541be39e0932595__section_wbj_5zf_zyb"/>

## Parameters

None



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



## Examples

This example uses the sa\_get\_user\_status system procedure to return the status of all database users.

```
CALL sa_get_user_status;
```


<table>
<tr>
<th valign="top">

user\_id

</th>
<th valign="top">

user\_name

</th>
<th valign="top">

connections

</th>
<th valign="top">

failed\_logins

</th>
<th valign="top">

last\_login\_time

</th>
<th valign="top">

locked

</th>
<th valign="top">

reason\_locked

</th>
</tr>
<tr>
<td valign="top">

0

</td>
<td valign="top">

SYS

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

PUBLIC

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

dbo

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

03:00.0

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

diagnostics

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

USER1

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

USER2

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

 

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

101

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>


<table>
<tr>
<th valign="top" colspan="5">

\(Continued\)

</th>
</tr>
<tr>
<th valign="top">

user\_dn

</th>
<th valign="top">

user\_dn\_cached\_at

</th>
<th valign="top">

password\_change\_state

</th>
<th valign="top">

password\_change\_first\_user

</th>
<th valign="top">

password\_change\_second\_user

</th>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
<td valign="top">

…

</td>
</tr>
</table>

