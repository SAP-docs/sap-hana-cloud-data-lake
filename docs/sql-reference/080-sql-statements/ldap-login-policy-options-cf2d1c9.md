<!-- copycf2d1c9435274f8189653106c440c633 -->

# LDAP Login Policy Options

Available login policy options for LDAP user authentication.




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

LDAP\_PRIMARY\_SERVER

</td>
<td valign="top">

Specifies the name of the primary LDAP server.

</td>
<td valign="top">

-   Values – N/A
-   Default – NULL
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

LDAP\_SECONDARY\_SERVER

</td>
<td valign="top">

Specifies the name of the secondary LDAP server.

</td>
<td valign="top">

-   Values – N/A
-   Default – NULL
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

LDAP\_AUTO\_FAILBACK\_PERIOD

</td>
<td valign="top">

Specifies the time period, in minutes, after which automatic failback to the primary server is attempted.

</td>
<td valign="top">

-   Values – 0–2147483647
-   Default – 15 minutes
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

LDAP\_FAILOVER\_TO\_STD

</td>
<td valign="top">

Permits authentication with standard authentication when authentication with the LDAP server fails because system resources, network outage, connection timeouts, or similar system failures. However, it does not permit an actual authentication failure returned from an LDAP server to fail over to standard authentication.

</td>
<td valign="top">

-   Values – ON; OFF
-   Default – ON
-   Applies to all users



</td>
</tr>
<tr>
<td valign="top">

LDAP\_REFRESH\_DN

</td>
<td valign="top">

Updates this value in the ISYSLOGINPOLICYOPTION system table with the current time, stored in Coordinated Universal Time \(UTC\).

Each time a user authenticates with LDAP, if the ldap\_refresh\_dn value in ISYSLOGINPOLICYOPTION is more recent than the user\_dn value of in ISYSUSER, a search for a new user DN occurs. The user\_dn value is then updated with the new user DN and the user\_dn\_changed\_at value is again updated to the current time.

</td>
<td valign="top">

-   Values – NOW
-   Initial value for CUSTOMER\_ROOT policy – NULL
-   Initial value for user-defined login policy – current time stored in UTC
-   Applies to all users



</td>
</tr>
</table>

