<!-- loioa615ad2284f21015b7ccab835341b235 -->

# COMMENT Statement for Data Lake Relational Engine

Stores a comment, in the system tables, about a database object.



> ### Restriction:  
> This data lake Relational Engine SQL statement can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
COMMENT ON
   { COLUMN [ <owner>.]<table-name>.<column-name>
   | EVENT <event-name>
   | EXTERNAL [ ENVIRONMENT ] OBJECT <object-name>
   | EXTERNAL ENVIRONMENT <environment-name>
   | EXTERNAL OBJECT <object-name>
   | FOREIGN KEY [ <owner>.]<table-name>.<role-name>
   | INDEX [ [ <owner>.]<table>.]<index-name>
   | INTEGRATED LOGIN <integrated-login-id>
   | JAVA CLASS <java-class-name>
   | JAVA JAR <java-jar-name>
   | LDAP SERVER <ldap-server-name>
   | LOGIN POLICY <policy-name>
   | MATERIALIZED VIEW [ <owner>.]<materialized-view-name>
   | PRIMARY KEY ON [ <owner>.]<table-name>
   | PROCEDURE [ <owner>.]<table-name>
   | ROLE <role-name>
   | SERVICE <web-service-name>
   | SEQUENCE [ <owner>.]<sequence-name>
   | TABLE [ <owner>.]<table-name>
   | TEXT CONFIGURATION [ < owner>.]<text-config-name>
   | TEXT INDEX <text-index-name> 
   | TRIGGER [ [ <owner>.]<table-name>.]<trigger-name>
   | USER <userid>
   | VIEW [ <owner>.]<view-name> }
   IS { <string> | NULL }
```

```
<environment-name> ::=
   { JAVA 
   | PERL 
   | PHP 
   | C_ESQL32 
   | C_ESQL64 
   | C_ODBC32 
   | C_ODBC64 }
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa615ad2284f21015b7ccab835341b235__IQ_Usage"/>

## Remarks

The COMMENT statement updates remarks in the ISYSREMARK system table. You can remove a comment by setting it to NULL. The owner of a comment on an index or trigger is the owner of the table on which the index or trigger is defined.

The COMMENT ON JAVA JAR, and COMMENT ON JAVA CLASS statements allow you to set the Remarks column in the SYS.ISYSREMARK system table. Remove a comment by setting it to NULL.

You cannot add comments for local temporary tables.



<a name="loioa615ad2284f21015b7ccab835341b235__IQ_Permissions"/>

## Privileges

The privilege required varies by clause. 


<table>
<tr>
<th valign="top">

Clause



</th>
<th valign="top">

Privilege Required



</th>
</tr>
<tr>
<td valign="top">

COLUMN



</td>
<td valign="top">

Requires one of:

-   You own the table
-   CREATE ANY TABLE system privilege
-   ALTER ANY TABLE system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

EVENT



</td>
<td valign="top">

Requires one of:

-   MANAGE ANY EVENT system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL \[ENVIRONMENT\] OBJECT



</td>
<td valign="top">

MANAGE ANY EXTERNAL OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

EXTERNAL ENVIRONMENT



</td>
<td valign="top">

MANAGE ANY EXTERNAL ENVIRONMENT system privilege



</td>
</tr>
<tr>
<td valign="top">

FOREIGN KEY



</td>
<td valign="top">

Requires one of:

-   You own the table
-   CREATE ANY TABLE system privilege
-   ALTER ANY TABLE system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

INDEX



</td>
<td valign="top">

Requires one of:

-   You own the index
-   CREATE ANY INDEX system privilege
-   ALTER ANY INDEX system privilege
-   COMMENT ANY OBJECT system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

INTEGRATED LOGIN



</td>
<td valign="top">

MANAGE ANY USER system privilege



</td>
</tr>
<tr>
<td valign="top">

JAVA CLASS or JAVA JAR



</td>
<td valign="top">

MANAGE ANY EXTERNAL OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

LDAP SERVER



</td>
<td valign="top">

MANAGE ANY LDAP SERVER system privilege



</td>
</tr>
<tr>
<td valign="top">

LOGIN POLICY



</td>
<td valign="top">

MANAGE ANY LOGIN POLICY system privilege



</td>
</tr>
<tr>
<td valign="top">

PRIMARY KEY ON



</td>
<td valign="top">

Requires one of:

-   You own the table
-   CREATE ANY TABLE system privilege
-   ALTER ANY TABLE system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

PROCEDURE



</td>
<td valign="top">

Requires one of:

-   You own the procedure
-   CREATE ANY PROCEDURE system privilege
-   ALTER ANY PROCEDURE system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

SEQUENCE



</td>
<td valign="top">

Requires one of:

-   You own the sequence
-   CREATE ANY SEQUENCE system privilege
-   ALTER ANY SEQUENCE system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

SERVICE



</td>
<td valign="top">

MANAGE ANY WEB SERVICE system privilege



</td>
</tr>
<tr>
<td valign="top">

ROLE



</td>
<td valign="top">

System role – administrative privilege over the role being commented on.

User-defined role – MANAGE ROLES system privilege or administrative privilege over the role being commented on.



</td>
</tr>
<tr>
<td valign="top">

TABLE



</td>
<td valign="top">

Requires one of:

-   You own the table
-   CREATE ANY TABLE system privilege
-   ALTER ANY TABLE system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

TEXT CONFIGURATION



</td>
<td valign="top">

Requires one of:

-   You created the text configuration
-   CREATE ANY TEXT CONFIGURATION system privilege
-   ALTER ANY TEXT CONFIGURATION system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

TEXT INDEX



</td>
<td valign="top">

Requires one of:

-   You created the text index
-   CREATE ANY INDEX system privilege
-   ALTER ANY INDEX system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

TRIGGER



</td>
<td valign="top">

Requires one of:

-   You created the trigger
-   CREATE ANY TRIGGER system privilege
-   ALTER ANY TRIGGER system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
<tr>
<td valign="top">

USER



</td>
<td valign="top">

MANAGE ANY USER system privilege



</td>
</tr>
<tr>
<td valign="top">

VIEW



</td>
<td valign="top">

Requires one of:

-   You own the view
-   CREATE ANY VIEW system privilege
-   ALTER ANY VIEW system privilege
-   CREATE ANY OBJECT system privilege
-   ALTER ANY OBJECT system privilege
-   COMMENT ANY OBJECT system privilege



</td>
</tr>
</table>

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) or [GRANT Object-Level Privilege Statement for Data Lake Relational Engine](grant-object-level-privilege-statement-for-data-lake-relational-engine-a3e154f.md) for assistance with granting privileges. 



<a name="loioa615ad2284f21015b7ccab835341b235__IQ_Standards"/>

## Standards

-   SQL – vendor extension to ISO/ANSI SQL grammar
-   SAP database products – not supported by SAP Adaptive Server Enterprise



<a name="loioa615ad2284f21015b7ccab835341b235__IQ_Examples"/>

## Examples

-   The following example adds a comment to the `Employees` table:

    ```
    COMMENT
    ON TABLE Employees 
    IS "Employee information"
    ```

-   The following example removes the comment from the `Employees` table:

    ```
    COMMENT
    ON TABLE Employees 
    IS NULL
    ```


**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[REVOKE Object-Level Privilege Statement for Data Lake Relational Engine](revoke-object-level-privilege-statement-for-data-lake-relational-engine-a3e7af2.md "Removes object-level privileges that were given using the GRANT statement.")

