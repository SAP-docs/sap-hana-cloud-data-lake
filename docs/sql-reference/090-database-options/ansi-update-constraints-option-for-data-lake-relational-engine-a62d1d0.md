<!-- loioa62d1d0684f21015aea99796080bc84e -->

# ANSI\_UPDATE\_CONSTRAINTS Option for Data Lake Relational Engine

Controls the range of updates that are permitted.



<a name="loioa62d1d0684f21015aea99796080bc84e__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62d1d0684f21015aea99796080bc84e__section_u1n_l5b_qkb"/>

## Syntax

```
ANSI_UPDATE_CONSTRAINTS = { OFF | CURSORS | STRICT };
```



<a name="loioa62d1d0684f21015aea99796080bc84e__iq_refso_344"/>

## Allowed Values

OFF, CURSORS, STRICT



<a name="loioa62d1d0684f21015aea99796080bc84e__iq_refso_345"/>

## Default

CURSORS



<a name="loioa62d1d0684f21015aea99796080bc84e__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



## Scope


<table>
<tr>
<th valign="top">

 

</th>
<th valign="top">

PUBLIC Role

</th>
<th valign="top">

For Current User

</th>
<th valign="top">

For Other Users

</th>
</tr>
<tr>
<td valign="top">

Allowed to set permanently?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Yes \(current connection only\)

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loioa62d1d0684f21015aea99796080bc84e__iq_refso_346"/>

## Remarks

Data lake Relational Engine provides several extensions that allow updates that are not permitted by the ANSI SQL standard. These extensions provide powerful, efficient mechanisms for performing updates. However, in some cases, they cause behavior that is not intuitive. This behavior might produce anomalies such as lost updates if the user application is not designed to expect the behavior of these extensions.

ANSI\_UPDATE\_CONSTRAINTS controls whether updates are restricted to those permitted by the SQL92 standard.

If the option is set to STRICT, these updates are prevented:

-   Updates of cursors containing JOINS
-   Updates of columns that appear in an ORDER BY clause
-   The FROM clause is not allowed in UPDATE statements.

If the option is set to CURSORS, these same restrictions are in place, but only for cursors. If a cursor is not opened with FOR UPDATE or FOR READ ONLY, the database server determines whether updates are permitted based on the SQL92 standard.

If ANSI\_UPDATE\_CONSTRAINTS is set to CURSORS or STRICT, cursors containing an ORDER BY clause default to FOR READ ONLY; otherwise, they continue to default to FOR UPDATE.



<a name="loioa62d1d0684f21015aea99796080bc84e__iq_refso_347"/>

## Examples

This code has a different effect, depending on the setting of ANSI\_UPDATE\_CONSTRAINTS:

```
CREATE TABLE mmg (a CHAR(3));
CREATE TABLE mmg1 (b CHAR(3));
```

```
INSERT INTO mmg VALUES ('001');
INSERT INTO mmg VALUES ('002');
INSERT INTO mmg VALUES ('003')
INSERT INTO mmg1 VALUES ('003');
SELECT * FROM mmg;
SELECT * FROM mmg1;
```



### Option 1

Set ANSI\_UPDATE\_CONSTRAINTS to STRICT:

```
SET OPTION public.Ansi_update_constraints = 'strict';
DELETE MMG FROM MMG1 WHERE A=B;
```

This results in an error indicating that the attempted update operation is not allowed.



### Option 2

Set ANSI\_UPDATE\_CONSTRAINTS to CURSORS or OFF:

```
SET OPTION public.Ansi_update_constraints = 'CURSORS';  // or 'OFF'
DELETE mmg FROM mmg1 WHERE A=B;
```

In this case, the deletion should complete without the error.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[UPDATE Statement for Data Lake Relational Engine](../080-sql-statements/update-statement-for-data-lake-relational-engine-a628441.md "Modifies existing rows of a single table, or a view that contains only one table.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

