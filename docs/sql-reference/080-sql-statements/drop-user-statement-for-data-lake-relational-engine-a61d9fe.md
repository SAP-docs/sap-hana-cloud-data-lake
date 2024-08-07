<!-- loioa61d9fe384f21015af5de6ef9830eeb0 -->

# DROP USER Statement for Data Lake Relational Engine

Removes a user.



<a name="loioa61d9fe384f21015af5de6ef9830eeb0__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
DROP USER <user-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa61d9fe384f21015af5de6ef9830eeb0__drop_user_remarks1"/>

## Remarks

When dropping a user, any permissions granted by this user are also removed. If the user being deleted owns any objects in the database, an error message appears, and the command fails.

The user being removed can't be connected to the current multiplex node when the statement is executed. If the user is connected to the database on a different multiplex node, the connection is dropped.

The user being removed cannot be connected to the current MPX node when the statement is executed. If the user is connected to the database on a different MPX node, the connection is be dropped.



<a name="loioa61d9fe384f21015af5de6ef9830eeb0__drop_user_priv1"/>

## Privileges



### 

Requires the MANAGE ANY USER system privilege.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.



<a name="loioa61d9fe384f21015af5de6ef9830eeb0__drop_user_standards1"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa61d9fe384f21015af5de6ef9830eeb0__drop_user_examples1"/>

## Examples

The following example drops the user `SQLTester` from the database:

```
DROP USER SQLTester;
```

**Related Information**  


[CREATE USER Statement for Data Lake Relational Engine](create-user-statement-for-data-lake-relational-engine-a619a5f.md "Creates a user.")

[ALTER USER Statement for Data Lake Relational Engine](alter-user-statement-for-data-lake-relational-engine-a6139f4.md "Changes user settings.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[DROP USER Statement for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2024_3_QRC/en-US/d94380cc72f2455b9c92809eee051a5a.html "Removes a user.") :arrow_upper_right:

