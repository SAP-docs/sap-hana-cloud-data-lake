<!-- loioa3e3fc8084f2101599d0afbadc8092b4 -->

# GRANT CHANGE PASSWORD Statement for Data Lake Relational Engine

Allows users to manage passwords for other users and administer the CHANGE PASSWORD system privilege.



Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
GRANT CHANGE PASSWORD ( { <target_user_list> | ANY | ANY WITH ROLES <target_role_list> } )
   TO <user_id>[, …]
   [ { WITH ADMIN [ ONLY ] OPTION | WITH NO ADMIN OPTION } ]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3e3fc8084f2101599d0afbadc8092b4__IQ_Parameters"/>

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



</dd><dt><b>

WITH ADMIN OPTION

</b></dt>
<dd>

\(Valid with the ANY clause only\) The user can both manage passwords and grant the CHANGE PASSWORD system privilege to another user.



</dd><dt><b>

WITH ADMIN ONLY OPTION

</b></dt>
<dd>

\(Valid with the ANY clause only\) The user can grant the CHANGE PASSWORD system privilege to another user, but cannot manage passwords of other users.



</dd><dt><b>

WITH NO ADMIN OPTION

</b></dt>
<dd>

The user can manage passwords, but cannot grant the CHANGE PASSWORD system privilege to another user.



</dd>
</dl>



<a name="loioa3e3fc8084f2101599d0afbadc8092b4__IQ_Usage"/>

## Remarks

A user can be granted the ability to manage the password of any user in the database \(ANY\) or only specific users \(*<target\_users\_list\>*\) or members of specific roles \(ANY WITH ROLES *<target\_roles\_list\>*\). Administrative rights to the CHANGE PASSWORD system privilege can only be granted when using the ANY clause.

If no clause is specified, ANY is used by default. If no administrative clause is specified in the grant statement, the WITH NO ADMIN OPTION clause is used.

By default, the CHANGE PASSWORD system privilege is granted to the SYS\_AUTH\_SA\_ROLE compatibility role with the WITH NO ADMIN OPTION clause and to the SYS\_AUTH\_SSO\_ROLE compatibility role with the ADMIN ONLY OPTION clause, if they exist.

Each target user specified \(target\_users\_list\) must be an existing user or user-extended role with a login password. Each target role specified \(target\_roles\_list\) must be an existing user-extended or user-defined role.



<a name="loioa3e3fc8084f2101599d0afbadc8092b4__IQ_Permissions"/>

## Privileges

Requires the CHANGE PASSWORD system privilege granted with administrative rights.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa3e3fc8084f2101599d0afbadc8092b4__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa3e3fc8084f2101599d0afbadc8092b4__IQ_Examples"/>

## Examples

-   The following example grants `Sally` and `Laurel` the ability to manage the password of `Bob`, `Sam`, and `Peter`:

    ```
    GRANT CHANGE PASSWORD (Bob, Sam, Peter) TO (Sally, Laurel)
    ```

-   The following example grants `Mary` the right to grant the CHANGE PASSWORD system privilege to any user in the database. However, since the system privilege is granted with the WITH ADMIN ONLY OPTION clause, `Mary` cannot manage the password of any other user.

    ```
    GRANT CHANGE PASSWORD (ANY) TO Mary WITH ADMIN ONLY OPTION
    ```

-   The following example grants `Steve` and `Joe` the ability to manage the password of any member of `Role1` or `Role2`:

    ```
    GRANT CHANGE PASSWORD (ANY WITH ROLES Role1, Role2) TO Steve, Joe
    ```


**Related Information**  


[REVOKE CHANGE PASSWORD Statement for Data Lake Relational Engine](revoke-change-password-statement-for-data-lake-relational-engine-a4277db.md "Removes the ability of a user to manage passwords and administer the system privilege.")

