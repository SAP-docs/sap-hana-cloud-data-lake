<!-- loio157fee58dd274f68ae00a61bffe8d9b0 -->

# MIN\_NUMERIC\_DIVISION\_SCALE Option for Data Lake Relational Engine

Controls the number of decimal places displayed for division operations on constant numeric values.



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__section_zx3_g24_hrb"/>

## Syntax

```
MIN_NUMERIC_DIVISION_SCALE = <value>;
```



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__iq_refso_771"/>

## Allowed Values

0 to 125



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__iq_refso_772"/>

## Default

6



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__iq_refso_773"/>

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



<a name="loio157fee58dd274f68ae00a61bffe8d9b0__iq_refso_774"/>

## Remarks

By default, queries on IQ main store tables use a six digit scale for division operations on constant numbers. Since IQ catalog store uses the same scale, there is minimal impact when comparing the values between stores, particularly when results are passed to numeric functions like POWER\(\), EXP\(\), etc.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

