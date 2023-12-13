<!-- loioa6337ae984f21015aed0c8058f0d84c1 -->

# DEFAULT\_DBSPACE Option for Data Lake Relational Engine

Changes the default dbspace where tables are created.



<a name="loioa6337ae984f21015aed0c8058f0d84c1__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa6337ae984f21015aed0c8058f0d84c1__section_zx3_g24_hrb"/>

## Syntax

```
DEFAULT_DBSPACE = <dbspace-name>;
```



<a name="loioa6337ae984f21015aed0c8058f0d84c1__iq_refso_476"/>

## Allowed Values

String containing a dbspace name



<a name="loioa6337ae984f21015aed0c8058f0d84c1__iq_refso_477"/>

## Default

'' \(the empty string\)



<a name="loioa6337ae984f21015aed0c8058f0d84c1__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa6337ae984f21015aed0c8058f0d84c1__iq_refso_478"/>

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



<a name="loioa6337ae984f21015aed0c8058f0d84c1__iq_refso_479"/>

## Remarks

DEFAULT\_DBSPACE allows the administrator to set the default dbspace for a role or user or allows a user to set the user’s own default dbspace.

IQ\_SYSTEM\_TEMP is always used for global temporary tables unless a table IN clause is used that specifies SYSTEM, in which case an SA global temporary table is created.

At database creation, the system dbspace, IQ\_SYSTEM\_MAIN, is created and is implied when the PUBLIC.DEFAULT\_DBSPACE option setting is empty or explicitly set to IQ\_SYSTEM\_MAIN. Immediately after creating the database, create a second main dbspace, revoke CREATE privilege in dbspace IQ\_SYSTEM\_MAIN from PUBLIC, grant CREATE in dbspace for the new main dbspace to selected users or PUBLIC, and set PUBLIC.DEFAULT\_DBSPACE to the new main dbspace. For example:

```
CREATE DBSPACE user_main USING FILE user_main
'user_main1' SIZE 10000;
GRANT CREATE ON user_main TO PUBLIC;
REVOKE CREATE ON IQ_SYSTEM_MAIN FROM PUBLIC;
SET OPTION PUBLIC.DEFAULT_DBSPACE = 'user_main';
```



<a name="loioa6337ae984f21015aed0c8058f0d84c1__iq_refso_480"/>

## Example

In this example, CONNECT and RESOURCE privileges on all dbspaces are granted to users usrA and usrB, and each of these users is granted CREATE privilege on a particular dbspace:

```
GRANT CONNECT, RESOURCE TO usrA, usrB
   IDENTIFIED BY pwdA, pwdB;
GRANT CREATE ON dbsp1 TO usrA;
GRANT CREATE ON dbsp3 TO usrB;
SET OPTION “usrA”.default_dbspace = ‘dbsp1’;
SET OPTION “usrB”.default_dbspace = ‘dbsp3’;
SET OPTION “PUBLIC”.default_dbspace = dbsp2;

CREATE TABLE “DBA”.t1(c1 int, c2 int);
INSERT INTO t1 VALUES (1, 1);
INSERT INTO t1 VALUES (2, 2);
COMMIT;
```

UsrA connects:

```
CREATE TABLE “UsrA”.t1(c1 int, c2 int);
INSERT INTO t1 VALUES (1, 1);
INSERT INTO t1 VALUES (2, 2);
COMMIT;
```

UsrB connects:

```
CREATE TABLE “UsrB”.t1(c1 int, c2 int);
INSERT INTO t1 VALUES (1, 1);
INSERT INTO t1 VALUES (2, 2);
COMMIT;
```

DBA connects:

```
SELECT Object, DbspaceName, ObjSize 
FROM sp_iqindexinfo();
```

sp\_iqindexinfo result:

```
DBA.t1                            dbsp2        200k
DBA.t1.ASIQ_IDX_T730_C1_FP        dbsp2        288k
DBA.t1.ASIQ_IDX_T730_C2_FP        dbsp2        288k
usrA.t1                           dbsp1        200k
usrA.t1.ASIQ_IDX_T731_C1_FP       dbsp1        288k
usrA.t1.ASIQ_IDX_T731_C2_FP       dbsp1        288k
usrB.t1                           dbsp3        200k
usrB.t1.ASIQ_IDX_T732_C1_FP       dbsp3        288k
usrB.t1.ASIQ_IDX_T732_C2_FP       dbsp3        288k
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

