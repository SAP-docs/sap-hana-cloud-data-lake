<!-- loioa63dca6484f2101581fcb6fb81ae842d -->

# MAX\_CLIENT\_NUMERIC\_SCALE Option for Data Lake Relational Engine

Controls the maximum scale for numeric data sent to the client.



<a name="loioa63dca6484f2101581fcb6fb81ae842d__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63dca6484f2101581fcb6fb81ae842d__section_zx3_g24_hrb"/>

## Syntax

```
MAX_CLIENT_NUMERIC_SCALE  = <value>;
```



<a name="loioa63dca6484f2101581fcb6fb81ae842d__iq_refso_718"/>

## Allowed Values

0 to 126



<a name="loioa63dca6484f2101581fcb6fb81ae842d__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63dca6484f2101581fcb6fb81ae842d__iq_refso_719"/>

## Default

0



<a name="loioa63dca6484f2101581fcb6fb81ae842d__iq_refso_720"/>

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



<a name="loioa63dca6484f2101581fcb6fb81ae842d__iq_refso_721"/>

## Remarks

When data lake Relational Engine performs its calculation, it promotes data types to an appropriate scale and size that ensure accuracy. The promoted data type might be larger than the original defined data size. You can set this option to the scale you want for numeric results.

Multiplication, division, addition, subtraction, and aggregate functions can all have results that exceed the maximum precision and scale.

For example, when a DECIMAL\(88,2\) is multiplied with a DECIMAL\(59,2\), the result could require a DECIMAL\(147,4\). With MAX\_CLIENT\_NUMERIC\_PRECISION of 126, only 126 digits are kept in the result. If MAX\_CLIENT\_NUMERIC\_SCALE is 4, the results are returned as a DECIMAL\(126,4\). If MAX\_CLIENT\_NUMERIC\_SCALE is 2, the results are returned as a DECIMAL\(126,2\). In both cases, there is a possibility for overflow.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[MAX\_CLIENT\_NUMERIC\_PRECISION Option for Data Lake Relational Engine](max-client-numeric-precision-option-for-data-lake-relational-engine-a63d9ba.md "Controls the maximum precision for numeric data sent to the client.")

[SCALE Option for Data Lake Relational Engine](scale-option-for-data-lake-relational-engine-a654041.md "Specifies the minimum number of digits after the decimal point when an arithmetic result is truncated to the maximum PRECISION, for queries on the catalog store only.")

