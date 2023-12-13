<!-- loioa648b25a84f210159df4edd5d6158c2d -->

# PRECISION Option for Data Lake Relational Engine

Specifies the maximum number of digits in the result of any decimal arithmetic, for queries on the catalog store only.



<a name="loioa648b25a84f210159df4edd5d6158c2d__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa648b25a84f210159df4edd5d6158c2d__section_zx3_g24_hrb"/>

## Syntax

```
PRECISION = <value>;
```



<a name="loioa648b25a84f210159df4edd5d6158c2d__iq_refso_838"/>

## Allowed Values

1 to 127



<a name="loioa648b25a84f210159df4edd5d6158c2d__iq_refso_839"/>

## Default

126



<a name="loioa648b25a84f210159df4edd5d6158c2d__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa648b25a84f210159df4edd5d6158c2d__iq_refso_840"/>

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

No

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Allowed to set temporarily?

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
<td valign="top">

No

</td>
</tr>
</table>



<a name="loioa648b25a84f210159df4edd5d6158c2d__iq_refso_841"/>

## Remarks

Precision is the total number of digits to the left and right of the decimal point. The default PRECISION value is fixed at 126. The SCALE option specifies the minimum number of digits after the decimal point, when an arithmetic result is truncated to the maximum specified by PRECISION, for queries on the catalog store.

> ### Note:  
> For IQ catalog store tables, the maximum value supported for the numeric function is 255. If the precision of the numeric function exceeds the maximum value supported, you see the following error message:
> 
> ```
> The result datatype for function '_funcname' exceeds the maximum 
> supported numeric precision of 255. Please set the proper value for 
> precision in numeric function, 'location'
> ```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SCALE Option for Data Lake Relational Engine](scale-option-for-data-lake-relational-engine-a654041.md "Specifies the minimum number of digits after the decimal point when an arithmetic result is truncated to the maximum PRECISION, for queries on the catalog store only.")

[MAX\_CLIENT\_NUMERIC\_PRECISION Option for Data Lake Relational Engine](max-client-numeric-precision-option-for-data-lake-relational-engine-a63d9ba.md "Controls the maximum precision for numeric data sent to the client.")

