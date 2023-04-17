<!-- loioa646abec84f210159912e1233d9fe2a3 -->

# ON\_TSQL\_ERROR Option \[TSQL\] for Data Lake Relational Engine

Controls error handling in stored procedures.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa646abec84f210159912e1233d9fe2a3__section_zx3_g24_hrb"/>

## Syntax

```
ON_TSQL_ERROR = <value>
```



<a name="loioa646abec84f210159912e1233d9fe2a3__iq_refso_820"/>

## Allowed Values

-   STOP – stops execution immediately upon finding an error.
-   CONDITIONAL – if the procedure uses ON EXCEPTION RESUME, and the statement following the error handles the error, continue; otherwise, exit.
-   CONTINUE – continue execution, regardless of the following statement. If there are multiple errors and the last statement executed was not successful, then the first error encountered in the stored procedure is returned once the procedure completes. This option most closely mirrors SAP Adaptive Server Enterprise behavior.



<a name="loioa646abec84f210159912e1233d9fe2a3__iq_refso_821"/>

## Default

CONDITIONAL



<a name="loioa646abec84f210159912e1233d9fe2a3__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa646abec84f210159912e1233d9fe2a3__iq_refso_325"/>

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



<a name="loioa646abec84f210159912e1233d9fe2a3__iq_refso_822"/>

## Remarks

ON\_TSQL\_ERROR controls error handling in stored procedures.

Both CONDITIONAL and CONTINUE settings for ON\_TSQL\_ERROR are used for SAP ASE compatibility, with CONTINUE most closely simulating SAP ASE behavior. The CONDITIONAL setting is recommended, particularly when developing new Transact-SQL stored procedures, as CONDITIONAL allows errors to be reported earlier.

When this option is set to STOP or CONTINUE, it supersedes the setting of the CONTINUE\_AFTER\_RAISERROR option. However, when this option is set to CONDITIONAL \(the default\), behavior following a RAISERROR statement is determined by the setting of the CONTINUE\_AFTER\_RAISERROR option.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[CREATE PROCEDURE Statement for Data Lake Relational Engine](../080-sql-statements/create-procedure-statement-for-data-lake-relational-engine-a6185b2.md "Creates a new user-defined SQL procedure in the database.")

[CREATE PROCEDURE Statement \[T-SQL\] for Data Lake Relational Engine](../080-sql-statements/create-procedure-statement-t-sql-for-data-lake-relational-engine-a618891.md "Creates a new procedure that is compatible with SAP Adaptive Server Enterprise.")

[RAISERROR Statement \[T-SQL\] for Data Lake Relational Engine](../080-sql-statements/raiserror-statement-t-sql-for-data-lake-relational-engine-a6227d8.md "Allows user-defined errors to be signaled, and sends a message on the client.")

[CONTINUE\_AFTER\_RAISERROR Option \[TSQL\] for Data Lake Relational Engine](continue-after-raiserror-option-tsql-for-data-lake-relational-engine-a62fea0.md "Controls behavior following a RAISERROR statement.")

