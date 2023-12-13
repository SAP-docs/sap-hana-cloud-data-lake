<!-- copy7fb8e4570f8946c5afbb6acf08e22dbf -->

# Login Policy Options

Available options for CUSTOMER\_ROOT and user-defined login policies.




<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
<th valign="top">

Properties

</th>
</tr>
<tr>
<td valign="top">

AUTO\_UNLOCK\_TIME

</td>
<td valign="top">

The time period after which locked accounts not granted the MANAGE ANY USER system privilege are automatically unlocked. You can define this option in any login policy.

</td>
<td valign="top">

-   Values – 0 – UNLIMITED
-   Default – UNLIMITED
-   Applies to all users without the MANAGE ANY USER system privilege



</td>
</tr>
<tr>
<td valign="top">

CHANGE\_PASSWORD\_DUAL\_CONTROL

</td>
<td valign="top">

Requires input from two users, each of whom is granted the CHANGE PASSWORD system privilege, to change the password of another user.

</td>
<td valign="top">

-   Values – ON; OFF
-   Default – OFF
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

LOCKED

</td>
<td valign="top">

If set ON, then users can’t establish new connections. This setting temporarily denies access to users of the login policy.

</td>
<td valign="top">

-   Values – ON; OFF
-   Default – OFF
-   Applies to all users without with the MANAGE ANY USER system privilege



</td>
</tr>
<tr>
<td valign="top">

LOGIN\_MODE

</td>
<td valign="top">

Control authentication methods for different sets of users.

> ### Note:  
> The LOGIN\_MODE value supersedes the LOGIN\_MODE public option value \(if the public option is set\). For information on the LOGIN\_MODE public option, see [LOGIN\_MODE Option for Data Lake Relational Engine \(Deprecated\)](../090-database-options/login-mode-option-for-data-lake-relational-engine-deprecated-a63cd19.md).
> 
> Restricting the LOGIN\_MODE to a single mode in a mixed environment \(for example, LDAPUA only\) restricts connections to only those users granted the corresponding login mapping. Attempts to connect using other methods generate an error.
> 
> Restricting the LOGIN\_MODE to LDAPUA only may result in a configuration where no users can connect to the server if no user or login policy exists that permits LDAPUA.



</td>
<td valign="top">

Accepts an individual value, or a comma-separated list, composed of:

-   Values:
    -   NULL – defaults to the CUSTOMER\_ROOT login policy of the database.
    -   Standard – password-based authentication
    -   JWT – all logins to the database must be made using JWT authentication.
    -   LDAPUA – all logins to the database must be made using LDAP logins.
    -   X509 – all logins to the database must be made using X.509 authentication.

-   Default – NULL

For example, "Standard,X509"

</td>
</tr>
<tr>
<td valign="top">

MAX\_CONNECTIONS

</td>
<td valign="top">

The maximum number of concurrent connections allowed for a user.

</td>
<td valign="top">

-   Values – 0 - UNLIMITED
-   Default – UNLIMITED
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

MAX\_DAYS\_SINCE\_LOGIN

</td>
<td valign="top">

The maximum elapsed days since the last login. Once the maximum days + 1 day is reached, the user account is locked.

</td>
<td valign="top">

-   Values – 0 - 2147483647
-   Default – UNLIMITED
-   Applies to all users without the MANAGE ANY USER system privilege



</td>
</tr>
<tr>
<td valign="top">

MAX\_FAILED\_LOGIN\_ATTEMPTS

</td>
<td valign="top">

The maximum number of failed attempts, since the last successful attempt, to log in before the account is locked.

</td>
<td valign="top">

-   Values – 0 - 2147483647
-   Default – UNLIMITED
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_EXPIRY\_ON\_NEXT\_LOGIN

</td>
<td valign="top">

If set ON, then the user's password expires at the next login.

</td>
<td valign="top">

-   Values – ON; OFF
-   Default – OFF
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

PASSWORD\_LIFE\_TIME

</td>
<td valign="top">

The maximum number of days before a password must be changed.

</td>
<td valign="top">

-   Values – 0 - 180
-   Default – 180
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

X509\_LIFE\_TIME

</td>
<td valign="top">

The maximum number of minutes that an X.509 certificate will remain valid for authentication.

</td>
<td valign="top">

-   Values – 0 - 259200 minutes
-   Default – 259200 minutes \(180 days\)
-   Applies to all users



</td>
</tr>
</table>

