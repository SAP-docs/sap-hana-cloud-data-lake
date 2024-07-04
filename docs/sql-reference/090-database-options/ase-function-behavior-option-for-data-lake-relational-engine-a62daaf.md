<!-- loioa62daafc84f21015b621feed0116ead6 -->

# ASE\_FUNCTION\_BEHAVIOR Option for Data Lake Relational Engine

Specifies that output of data lake Relational Engine functions, including INTTOHEX and HEXTOINT, is consistent with the output of SAP Adaptive Server Enterprise functions.



<a name="loioa62daafc84f21015b621feed0116ead6__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62daafc84f21015b621feed0116ead6__section_u1n_l5b_qkb"/>

## Syntax

```
ASE_FUNCTION_BEHAVIOR = { ON | OFF };
```



<a name="loioa62daafc84f21015b621feed0116ead6__iq_refso_358"/>

## Allowed Values

ON, OFF



<a name="loioa62daafc84f21015b621feed0116ead6__iq_refso_359"/>

## Default

OFF



<a name="loioa62daafc84f21015b621feed0116ead6__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62daafc84f21015b621feed0116ead6__iq_refso_360"/>

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



<a name="loioa62daafc84f21015b621feed0116ead6__iq_refso_361"/>

## Remarks

When ASE\_BEHAVIOR\_FUNCTION is ON, some of the data lake Relational Engine data type conversion functions, including HEXTOINT and INTTOHEX, return output that is consistent with the output of SAP ASE functions. The differences in the SAP ASE and data lake Relational Engine output, with respect to formatting and length, exist because SAP ASE primarily uses signed 32-bit as the default and data lake Relational Engine primarily uses unsigned 64-bit as the default.

Data lake Relational Engine does not provide support for 64-bit integer, as SAP ASE does not have a 64-bit integer data type.



<a name="loioa62daafc84f21015b621feed0116ead6__iq_refso_362"/>

## Examples

In this example, the HEXTOINT function returns a different value based on whether ASE\_BEHAVIOR\_FUNCTION is ON or OFF.

The HEXTOINT function returns 4294967287 with ASE\_BEHAVIOR\_FUNCTION OFF:

```
select hextoint('fffffff7') from iq_dummy;
```

The HEXTOINT function returns -9 with ASE\_BEHAVIOR\_FUNCTION ON:

```
select hextoint('fffffff7') from iq_dummy;
```

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[CONVERSION\_ERROR Option \[TSQL\] for Data Lake Relational Engine](conversion-error-option-tsql-for-data-lake-relational-engine-a63018a.md "Controls reporting of data type conversion failures on fetching information from the database.")

[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

