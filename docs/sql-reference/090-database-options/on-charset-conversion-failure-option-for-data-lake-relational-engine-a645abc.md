<!-- loioa645abcb84f21015ab8891ab0425a318 -->

# ON\_CHARSET\_CONVERSION\_FAILURE Option for Data Lake Relational Engine

Controls the action taken, if an error is encountered during character conversion.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa645abcb84f21015ab8891ab0425a318__on_charset_conversion_failure_syntax1"/>

## Syntax

```
ON_CHARSET_CONVERSION_FAILURE = { IGNORE | WARNING | ERROR }
```



<a name="loioa645abcb84f21015ab8891ab0425a318__on_charset_conversion_failure_values1"/>

## Allowed Values

-   IGNORE – errors and warnings do not appear.
-   WARNING – substitutions and illegal characters are reported as warnings. Illegal characters are not translated.
-   ERROR – substitutions and illegal characters are reported as errors.



<a name="loioa645abcb84f21015ab8891ab0425a318__on_charset_conversion_failure_default1"/>

## Default

IGNORE



<a name="loioa645abcb84f21015ab8891ab0425a318__on_charset_conversion_failure_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa645abcb84f21015ab8891ab0425a318__on_charset_conversion_failure_scope1"/>

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



<a name="loioa645abcb84f21015ab8891ab0425a318__on_charset_conversion_failure_remarks1"/>

## Remarks

ON\_CHARSET\_CONVERSION\_FAILURE controls the action taken, if an error is encountered during character conversion.

Single-byte to single-byte converters are not able to report substitutions and illegal characters, and must be set to IGNORE.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[ON_CHARSET_CONVERSION_FAILURE Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/6ed545d21d7a4c159cabfdd39fcc9c73.html "Controls the action taken, if an error is encountered during character conversion.") :arrow_upper_right:

