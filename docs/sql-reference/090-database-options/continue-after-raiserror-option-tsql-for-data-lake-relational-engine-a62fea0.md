<!-- loioa62fea0a84f210159f28c35300877d0f -->

# CONTINUE\_AFTER\_RAISERROR Option \[TSQL\] for Data Lake Relational Engine

Controls behavior following a RAISERROR statement.



<a name="loioa62fea0a84f210159f28c35300877d0f__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62fea0a84f210159f28c35300877d0f__section_xdr_2ry_brb"/>

## Syntax

```
CONTINUE_AFTER_RAISERROR = { ON | OFF };
```



<a name="loioa62fea0a84f210159f28c35300877d0f__iq_refso_408"/>

## Allowed Values

ON, OFF



<a name="loioa62fea0a84f210159f28c35300877d0f__iq_refso_409"/>

## Default

ON



<a name="loioa62fea0a84f210159f28c35300877d0f__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62fea0a84f210159f28c35300877d0f__iq_refso_325"/>

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



<a name="loioa62fea0a84f210159f28c35300877d0f__iq_refso_410"/>

## Remarks

The RAISERROR statement is used within procedures to generate an error. When CONTINUE\_AFTER\_RAISERROR is set to OFF, the execution of the procedure is stopped when the RAISERROR statement is encountered.

When CONTINUE\_AFTER\_RAISERROR is ON, the RAISERROR statement no longer signals an execution-ending error. Instead, the RAISERROR status code and message are stored and the most recent RAISERROR is returned when the procedure completes. If the procedure that caused the RAISERROR was called from another procedure, the RAISERROR is not returned until the outermost calling procedure terminates.

Intermediate RAISERROR statuses and codes are lost after the procedure terminates. If, at return time, an error occurs along with the RAISERROR, then the error information is returned and the RAISERROR information is lost. The application can query intermediate RAISERROR statuses by examining @@error global variable at different execution points.

The setting of CONTINUE\_AFTER\_RAISERROR is used to control behavior following a RAISERROR statement only if the ON\_TSQL\_ERROR option is set to CONDITIONAL \(the default\). If you set the ON\_TSQL\_ERROR option to STOP or CONTINUE, the ON\_TSQL\_ERROR setting takes precedence over the CONTINUE\_AFTER\_RAISERROR setting.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[ON\_TSQL\_ERROR Option \[TSQL\] for Data Lake Relational Engine](on-tsql-error-option-tsql-for-data-lake-relational-engine-a646abe.md "Controls error handling in stored procedures.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

