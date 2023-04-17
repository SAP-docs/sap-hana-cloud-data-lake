<!-- loioa427feea84f21015941fe83a5ba6eb0b -->

# CREATE ROLE Statement for Data Lake Relational Engine

Creates a new role, extends an existing user to act as a role, or manages role administrators on a role.



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
CREATE [ OR REPLACE ] ROLE { <role_name> | FOR USER <user_id> }
   [ WITH ADMIN [ ONLY ] <admin_name> [...] , [ SYS_MANAGE_ROLES_ROLE ]
```



<a name="loioa427feea84f21015941fe83a5ba6eb0b__IQ_Parameters"/>

## Parameters

 *<role\_name\>*
 :   Unless you are using the OR REPLACE clause, *<role\_name\>* cannot already exist in the database.

  OR REPLACE
 :   *<role\_name\>* must already exist in the database. If *<role\_name\>* does not already exist, a new user-defined role is created. All current administrators are replaced by those specified in the *<admin\_name\>* clause as follows:

    -   All existing role administrators granted the WITH ADMIN OPTION not included on the new role administrators list become members of the role with no administrative rights on the role.
    -   All existing role administrators granted the WITH ADMIN ONLY OPTION not included on the new role administrators list are removed as members of the role.

    When using the OR REPLACE clause, if an existing role administrator is included on the new role administrators list he or she retains his or her original administrative rights if they are higher than the replacement rights. For example, User A is an existing role administrator originally granted WITH ADMIN rights on the role. New role administrators are granted WITH ADMIN ONLY rights. If User A is included on this list, User A retains the higher WITH ADMIN rights.

  FOR USER *<user\_id\>*
 :   When using the FOR USER clause without the OR REPLACE, *<user\_id\>* must be the name of an existing user that currently does not have the ability to act as a role.

  *<admin\_name\>*
 :   List of users to be designated administrators of the role.

  WITH ADMIN
 :   Each *<admin\_name\>* specified is granted administrative privileges over the role. They also inherit all underlying system privileges of the role. WITH ADMIN clause is not valid when SYS\_MANAGE\_ROLES\_ROLE is included on the list.

  WITH ADMIN ONLY
 :   Each *<admin\_name\>* specified is granted administrative privileges only over the role. They do not inherit the underlying system privileges of the role.

  SYS\_MANAGE\_ROLES\_ROLE
 :   Allows global role administrators to administer the role. Can be specified in conjunction with the WITH ADMIN ONLY clause.

 

<a name="loioa427feea84f21015941fe83a5ba6eb0b__IQ_Usage"/>

## Remarks

If you specify role administrators \(*<admin\_name\>*\), but do not include the global role administrator \(SYS\_MANAGE\_ROLES\_ROLE\), global role administrators will be unable to manage the new role. For this reason, do not specify role administrators during the creation process, but instead use the OR REPLACE clause to add them afterwards.

If you do not specify an ADMIN clause, the default WITH ADMIN ONLY clause is used and the default administrator is the global roles administrator \(SYS\_MANAGE\_ROLES\_ROLE\).

When replacing role administrators, if the role has a global role administrator, it must be included on the new role administrators list or it is removed from the role.

However, when using the WITH ADMIN clause to grant role administrators, since the clause is not valid for global role administrators, you must use the `GRANT ROLE` statement to re-add the global role administrator \(SYS\_MANAGE\_RILES\_ROLE\) to the role. Failure to perform this grant means global role administrators are unable to manage the role.



<a name="loioa427feea84f21015941fe83a5ba6eb0b__IQ_Permissions"/>

## Privileges

-   To create a new role requires the MANAGE ROLES system privilege.
-   To use the OR REPLACE clause requires:
    -   MANAGE ROLES system privilege
    -   Administrative rights over the role being replaced.


See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa427feea84f21015941fe83a5ba6eb0b__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension



<a name="loioa427feea84f21015941fe83a5ba6eb0b__IQ_Examples"/>

## Examples

-   The following example creates the role `Sales`. Only global role administrator can administer the role.

    ```
    CREATE ROLE Sales
    ```

-   The following example extends the existing user `Jane` to act as a role.

    ```
    CREATE OR REPLACE ROLE FOR USER Jane
    ```

-   The following example creates the role `Finance` with `Mary` and `Jeff` as role administrators with administrative rights to the role. Global role administrators cannot administer this role.

    ```
    CREATE ROLE Finance WITH ADMIN Mary, Jeff
    ```

-   The following example creates the role `Marketing` with `Mary` and `Jeff` as role administrators. Global role administrators can also manage this role.

    ```
    CREATE ROLE Finance 
    WITH ADMIN ONLY Mary, Jeff, SYS_MANAGE_ROLES_ROLE
    ```

-   In the following example, `Finance` is an existing role with `Harry` and `Susan` as role administrators with administrative rights. You want to keep `Susan` as an administrator, replace `Harry`, and add the global role administrator. The new role administrators will have administrative rights only. This statement keeps `Susan` as an administrator, but `Susan` retains administrative rights to the role since the original administrative rights granted were higher. `Harry` is replaced by `Bob` and `Sarah`, with administrative rights only, and the global role administrator is added to the role. `Harry` remains a member of the role, but has no administrative rights.

    ```
    CREATE OR REPLACE ROLE Finance 
    WITH ADMIN ONLY Susan, Bob, Sarah, SYS_MANAGE_ROLE_ROLE
    ```


**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[DROP ROLE Statement for Data Lake Relational Engine](drop-role-statement-for-data-lake-relational-engine-a42903c.md "Removes a user-defined role from the database or converts a user-extended role to a regular user.")

