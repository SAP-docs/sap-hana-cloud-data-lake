<!-- loiod94380cc72f2455b9c92809eee051a5a -->

# DROP USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Removes a user.



<a name="loiod94380cc72f2455b9c92809eee051a5a__section_pkx_2ns_nyb"/>

## Usage

This data lake Relational Engine \(SAP HANA DB-Managed\) SQL statement can be used when:

-   Connected directly to data lake Relational Engine **coordinator** as a data lake Relational Engine user. This syntax cannot be run using the REMOTE\_EXECUTE procedure.



```
DROP USER <user-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loiod94380cc72f2455b9c92809eee051a5a__section_yrw_rbp_vyb"/>

## Remarks

When dropping a user, any permissions granted by this user are also removed. If the user being deleted owns any objects in the database, an error message appears, and the command fails.

The user being removed can't be connected to the current multiplex node when the statement is executed. If the user is connected to the database on a different multiplex node, the connection is dropped.

The user being removed cannot be connected to the current MPX node when the statement is executed. If the user is connected to the database on a different MPX node, the connection is be dropped.



<a name="loiod94380cc72f2455b9c92809eee051a5a__section_hhl_sbp_vyb"/>

## Privileges



### 


<dl>
<dt><b>

Connected to SAP HANA database as a SAP HANA database user.:

</b></dt>
<dd>

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the SAP HANA database REMOTE\_EXECUTE procedure associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).

-   See [REMOTE\_EXECUTE Guidance and Examples for Executing SQL Statements](remote-execute-guidance-and-examples-for-executing-sql-statements-fd99ac0.md).




</dd>
</dl>



<a name="loiod94380cc72f2455b9c92809eee051a5a__section_x4x_sbp_vyb"/>

## Standards

-   SQL – ISO/ANSI SQL compliant
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loiod94380cc72f2455b9c92809eee051a5a__section_kp3_tbp_vyb"/>

## Examples

The following example drops the user `SQLTester` from the database:

```
DROP USER SQLTester;
```

**Related Information**  


[ALTER USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](alter-user-statement-for-data-lake-relational-engine-sap-hana-db-managed-a9da894.md "Changes user settings.")

[CREATE USER Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](create-user-statement-for-data-lake-relational-engine-sap-hana-db-managed-a21f652.md "Creates a user.")

[DROP USER Statement for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2024_3_QRC/en-US/a61d9fe384f21015af5de6ef9830eeb0.html "Removes a user.") :arrow_upper_right:

