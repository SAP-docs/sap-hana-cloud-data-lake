<!-- loioa63407dc84f210158c18c91e4587106b -->

# DEFAULT\_ISQL\_ENCODING Option \[Interactive SQL\] for Data Lake Relational Engine

Specifies the code page used by READ and OUTPUT statements.



<a name="loioa63407dc84f210158c18c91e4587106b__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63407dc84f210158c18c91e4587106b__section_zx3_g24_hrb"/>

## Syntax

```
DEFAULT_ISQL_ENCODING = <value>
```



<a name="loioa63407dc84f210158c18c91e4587106b__iq_refso_489"/>

## Allowed Values

*<identifier\>* or *<string\>*



<a name="loioa63407dc84f210158c18c91e4587106b__iq_refso_490"/>

## Default

Use system code page \(empty string\)



<a name="loioa63407dc84f210158c18c91e4587106b__section_kdj_f4g_kqb"/>

## Privileges

None



<a name="loioa63407dc84f210158c18c91e4587106b__iq_refso_491"/>

## Scope

Can only be set as a temporary option, for the duration of the current connection.



<a name="loioa63407dc84f210158c18c91e4587106b__iq_refso_492"/>

## Remarks

DEFAULT\_ISQL\_ENCODING specifies the code page to use when reading or writing files. It cannot be set permanently. The default code page is the default code page for the platform you are running on.

Interactive SQL determines the code page that is used for a particular OUTPUT or READ statement as follows, where code page values occurring earlier in the list take precedence over those occurring later in the list:

-   The code page specified in the ENCODING clause of the OUTPUT or READ statement
-   The code page specified with the DEFAULT\_ISQL\_ENCODING option \(if this option is set\)
-   The default code page for the computer on which Interactive SQL is running



<a name="loioa63407dc84f210158c18c91e4587106b__iq_refso_493"/>

## Example

Set the encoding to UTF-16 \(for reading Unicode files\):

```
SET TEMPORARY OPTION DEFAULT_ISQL_ENCODING = 'UTF-16'
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[OUTPUT Statement \[Interactive SQL\] for Data Lake Relational Engine](../080-sql-statements/output-statement-interactive-sql-for-data-lake-relational-engine-a62189f.md "Writes the information retrieved by the current query to a file.")

[READ Statement \[Interactive SQL\] for Data Lake Relational Engine](../080-sql-statements/read-statement-interactive-sql-for-data-lake-relational-engine-a622ae5.md "Reads Interactive SQL (dbisql) statements from a file.")

