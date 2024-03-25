<!-- loioa4277db384f21015b89afd8851d4c373 -->

# REVOKE CHANGE PASSWORD Statement for Data Lake Relational Engine

Removes the ability of a user to manage passwords and administer the system privilege.



<a name="loioa4277db384f21015b89afd8851d4c373__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE [ ADMIN OPTION FOR ] CHANGE PASSWORD
   [ ( { <target_user_list> 
       | ANY 
       | ANY WITH ROLES <target_role_list> } ) ]
   FROM <user_ID> [,...]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa4277db384f21015b89afd8851d4c373__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<target\_user\_list\>*

</b></dt>
<dd>

Users the grantee has the potential to impersonate. The list must consist of existing users or user-extended roles with login passwords. Separate the user\_IDs in the list with commas.



</dd><dt><b>

ANY

</b></dt>
<dd>

All database users with login passwords become potential target users to manage passwords for each grantee.



</dd><dt><b>

ANY WITH ROLES *<target\_role\_list\>*

</b></dt>
<dd>

List of target roles for each grantee. Any users who are granted any of the target roles become potential target users for each grantee. The *<target\_role\_list\>* must consist of existing roles and the users who are granted said roles must consist of database users with login passwords. Use commas to separate multiple user\_IDs.



</dd><dt><b>

*<user\_id\>*

</b></dt>
<dd>

Must be the name of an existing user or role that has a login password. Separate multiple user\_ids with commas.



</dd>
</dl>



<a name="loioa4277db384f21015b89afd8851d4c373__IQ_Usage"/>

## Remarks

Depending on how the CHANGE PASSWORD system privilege was initially granted, using the ADMIN OPTION FOR clause when revoking CHANGE PASSWORD has different results:


<table>
<tr>
<th valign="top">

Clause Used When CHANGE PASSWORD was Originally Granted

</th>
<th valign="top">

Result When Using ADMIN OPTION FOR when revoking CHANGE PASSWORD

</th>
</tr>
<tr>
<td valign="top">

The WITH ADMIN OPTION clause

</td>
<td valign="top">

Revokes only the ability to administer the CHANGE PASSWORD system privilege \(that is, grant the system privilege to another user\) — the ability to actually manage passwords for other users remains.

</td>
</tr>
<tr>
<td valign="top">

The WITH ADMIN ONLY OPTION clause

</td>
<td valign="top">

Semantically equivalent to revoking the entire CHANGE PASSWORD system privilege

</td>
</tr>
<tr>
<td valign="top">

The WITH NO ADMIN OPTION clause

</td>
<td valign="top">

Nothing is revoked because there were no administrative rights granted in the first place.

</td>
</tr>
</table>

You can revoke the CHANGE PASSWORD system privilege from any combination of users and roles granted.



<a name="loioa4277db384f21015b89afd8851d4c373__IQ_Permissions"/>

## Privileges

Requires the CHANGE PASSWORD system privilege granted with administrative rights.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa4277db384f21015b89afd8851d4c373__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa4277db384f21015b89afd8851d4c373__IQ_Examples"/>

## Examples

-   The following example removes the ability of `Joe` to manage the passwords of `Sally`or `Bob`:

    ```
    REVOKE CHANGE PASSWORD (Sally, Bob) FROM Joe;
    ```

-   The following example if the CHANGE PASSWORD system privilege was originally granted to `Sam` with the WITH ADMIN OPTION clause, this example removes the ability of `Sam` to grant the CHANGE PASSWORD system privilege to another user, but still allows `Sam` to manage passwords for those users specified in the original `GRANT CHANGE PASSWORD` statement. However, if the CHANGE PASSWORD system privilege was originally granted to `Sam` with the WITH ADMIN ONLY OPTION clause, this example removes all permissions to the system privilege from `Sam`.

    ```
    REVOKE ADMIN OPTION FOR CHANGE PASSWORD FROM Sam;
    ```


**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

