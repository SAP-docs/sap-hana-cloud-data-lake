<!-- loioa44d541d84f2101585ffc945ef610744 -->

# sa\_get\_ldapserver\_status System Procedure for Data Lake Relational Engine

Determines the current status of the LDAP server configuration object.



> ### Restriction:  
> This data lake Relational Engine procedure can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
sa_get_ldapserver_status()
```



<a name="loioa44d541d84f2101585ffc945ef610744__section_ghc_xjs_mbb"/>

## Result Set


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`ldsrv_id`



</td>
<td valign="top">

UNSIGNED BIGINT



</td>
<td valign="top">

A unique identifier for the LDAP server configuration object that is the primary key and is used by the login policy to refer to the LDAP server.



</td>
</tr>
<tr>
<td valign="top">

`ldsrv_name`



</td>
<td valign="top">

CHAR\(128\)



</td>
<td valign="top">

The name assigned to the LDAP server configuration object.



</td>
</tr>
<tr>
<td valign="top">

`ldsrv_state`



</td>
<td valign="top">

CHAR\(9\)



</td>
<td valign="top">

Read-only state of the LDAP server, A numeric value is stored in system table; a corresponding text value appears in the system view:

-   1 – RESET
-   2 – READY
-   3 – ACTIVE
-   4 – FAILED
-   5 – SUSPENDED



</td>
</tr>
<tr>
<td valign="top">

`ldsrv_last_state_change`



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Indicates the time the last state change occurred. The value is stored in Coordinated Universal Time \(UTC\), regardless of the local time zone of the LDAP server.



</td>
</tr>
</table>



<a name="loioa44d541d84f2101585ffc945ef610744__section_ps5_2ks_mbb"/>

## Remarks

To see SYSLDAPSERVER column values before a checkpoint occurs and the contents of memory are written to the catalog on disk.  The updates to the catalog columns ldsrv\_state and ldsrv\_last\_state\_change occur asynchronously during checkpoint to the LDAP server object as the result of an event that changes the LDAP server object state, such as a failed connection due to a failed LDAP directory server.  The LDAP server object state reflects the state of the LDAP directory server.



## Privileges

To run this procedure, you need the EXECUTE privilege on the procedure. See [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md).



<a name="loioa44d541d84f2101585ffc945ef610744__section_slh_xrs_mbb"/>

## Side Effects

None

