<!-- loioa3e6a6f984f2101598d781f74cd67db4 -->

# REVOKE CONNECT Statement for Data Lake Relational Engine

Removes a user from the database.



<a name="loioa3e6a6f984f2101598d781f74cd67db4__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
REVOKE CONNECT
   FROM <user_id> [,...]
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa3e6a6f984f2101598d781f74cd67db4__IQ_Parameters"/>

## Parameters


<dl>
<dt><b>

*<user\_id\>*

</b></dt>
<dd>

Must be the name of an existing user or role that has a login password. Separate multiple user\_IDs with commas.



</dd>
</dl>



<a name="loioa3e6a6f984f2101598d781f74cd67db4__IQ_Usage"/>

## Remarks

Use system procedures or CREATE USER and DROP USER statements, not `GRANT` and `REVOKE` statements, to add and remove user IDs.

You cannot revoke the connect privileges from a user if he or she owns database objects, such as tables. Attempting to do so with a `REVOKE` statement or `sp_iqdroplogin` stored procedure returns an error such as ***Cannot drop a user that owns tables in runtime system.***



<a name="loioa3e6a6f984f2101598d781f74cd67db4__IQ_Permissions"/>

## Privileges

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.

> ### Note:  
> If revoking CONNECT permissions or table permissions from another user, the target user cannot be connected to the database.



<a name="loioa3e6a6f984f2101598d781f74cd67db4__IQ_Standards"/>

## Standards

ANSI SQL – compliance level: Transact-SQL extension

**Related Information**  


[GRANT CONNECT Statement for Data Lake Relational Engine](grant-connect-statement-for-data-lake-relational-engine-a3e04cc.md "Create a new user, and can also be used to change a password. However, it is recommended that you use the CREATE USER statement to create users instead of the GRANT CONNECT statement.")

