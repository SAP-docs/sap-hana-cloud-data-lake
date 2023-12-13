<!-- loioa63018a284f210159f458fb9eec74501 -->

# CONVERSION\_ERROR Option \[TSQL\] for Data Lake Relational Engine

Controls reporting of data type conversion failures on fetching information from the database.



<a name="loioa63018a284f210159f458fb9eec74501__section_fq2_gpq_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63018a284f210159f458fb9eec74501__conversion_error_syntax1"/>

## Syntax

```
CONVERSION_ERROR = { ON | OFF };
```



<a name="loioa63018a284f210159f458fb9eec74501__conversion_eror_values1"/>

## Allowed Values

ON, OFF



<a name="loioa63018a284f210159f458fb9eec74501__conversion_error_default1"/>

## Default

ON



<a name="loioa63018a284f210159f458fb9eec74501__conversion_error_priv1"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63018a284f210159f458fb9eec74501__conversion_error_scope1"/>

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



<a name="loioa63018a284f210159f458fb9eec74501__conversion_error_remarks"/>

## Remarks

This option controls whether data type conversion failures, when data is fetched from the database or inserted into the database, are reported by the database as errors \(CONVERSION\_ERROR set to ON\), or as warnings \(CONVERSION\_ERROR set to OFF\).

When CONVERSION\_ERROR is set to ON, the SQLE\_CONVERSION\_ERROR error is generated.

If the option is set to OFF, the warning SQLE\_CANNOT\_CONVERT is produced. Each thread doing data conversion for a LOAD statement writes at most one warning message to the `.iqmsg` file.

If conversion errors are reported as warnings only, the NULL value is used in place of the value that could not be converted. In Embedded SQL, an indicator variable is set to -2 for the column or columns that cause the error.

> ### Note:  
> Data lake Relational Engine does not silently truncate the conversion result of numeric and date data types to CHAR and VARCHAR. A conversion error is generated when the following data types are converted to a string that is longer than the column width:
> 
> -   TINYINT, SMALLINT, \[UNSIGNED\] \{ INT | INTEGER \}, \[ UNSIGNED \] BIGINT
> -   NUMERIC, DECIMAL
> -   FLOAT, DOUBLE, REAL
> -   DATE, DATETIME, SMALLDATETIME, TIME, TIMESTAMP
> 
> The CONVERSION\_ERROR option controls data lake Relational Engine behavior in cases of conversion error. If you set the CONVERSION\_ERROR option to:
> 
> -   OFF – then data lake Relational Engine inserts a NULL value when possible
> 
> -   ON – then data lake Relational Engine rolls back the insert and logs a conversion error

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[CONVERSION_ERROR Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_4_QRC/en-US/b24b81f09e9a442d842dc39630105c9b.html "Controls reporting of data type conversion failures on fetching information from the database.") :arrow_upper_right:

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

