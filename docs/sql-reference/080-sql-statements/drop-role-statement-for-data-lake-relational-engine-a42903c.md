<!-- loioa42903c984f210159ad390495d594b47 -->

# DROP ROLE Statement for Data Lake Relational Engine

Removes a user-defined role from the database or converts a user-extended role to a regular user.



<a name="loioa42903c984f210159ad390495d594b47__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP ROLE [ FROM USER ] <role_name>
   [ WITH REVOKE ];
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa42903c984f210159ad390495d594b47__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<role\_name\>*

</b></dt>
<dd>

Must be the name of a role that already exists in the database.



</dd><dt><b>

FROM USER

</b></dt>
<dd>

Required to convert a user-extended role back to act as a regular user rather than remove it from the database. The *<role\_name\>* must exist in the database.

The user retains any login privileges, system privileges, and roles granted to the user-extended role and becomes the owner of any objects owned by the user-extended role. Any users granted to the user-extended are immediately revoked.



</dd><dt><b>

WITH REVOKE

</b></dt>
<dd>

Required when dropping a standalone or user-extended role to which users have been granted the underlying system privileges of the role. The grant can have been made with either the WITH ADMIN OPTION or WITH NO ADMIN OPTION clause.



</dd>
</dl>



<a name="loioa42903c984f210159ad390495d594b47__IQ_Usage"/>

## Remarks

A user-defined role can be dropped from the database or converted back to a regular user at any time as long as all dependent roles left meet the minimum required number of administrative users with active passwords.



<a name="loioa42903c984f210159ad390495d594b47__IQ_Permissions"/>

## Privileges

Requires administrative rights over the role being dropped. If the role being dropped owns objects, none are in use by any user in any session at the time the `DROP ROLE` statement is executed.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa42903c984f210159ad390495d594b47__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa42903c984f210159ad390495d594b47__IQ_Examples"/>

## Examples

-   The following example converts a user-extended role named `Joe` that has not been granted to other users or roles back to a regular user:

    ```
    DROP ROLE FROM USER Joe;
    ```

-   The following example drops a user-extended role named `Jack` that has not been granted to other users or roles from the database:

    ```
    DROP ROLE Jack;
    ```

-   The following example converts a user-extended role named `Sam` that has been granted to other user or roles back to a regular role:

    ```
    DROP ROLE FROM USER Sam
    WITH REVOKE;
    ```

-   The following example drops a standalone role named `Sales2` that has been granted to other users or roles from the database:

    ```
    DROP ROLE Sales2
    WITH REVOKE;
    ```


**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[CREATE ROLE Statement for Data Lake Relational Engine](create-role-statement-for-data-lake-relational-engine-a427fee.md "Creates a new role, extends an existing user to act as a role, or manages role administrators on a role.")

