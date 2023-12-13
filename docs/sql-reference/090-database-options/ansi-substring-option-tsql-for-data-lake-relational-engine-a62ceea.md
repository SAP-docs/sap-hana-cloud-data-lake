<!-- loioa62ceea984f210159d1a91e2823fa668 -->

# ANSI\_SUBSTRING Option \[TSQL\] for Data Lake Relational Engine

Controls the behavior of the SUBSTRING \(SUBSTR\) function when negative values are provided for the start or length parameters.



<a name="loioa62ceea984f210159d1a91e2823fa668__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa62ceea984f210159d1a91e2823fa668__section_u1n_l5b_qkb"/>

## Syntax

```
ANSI_SUBSTRING = { ON | OFF };
```



<a name="loioa62ceea984f210159d1a91e2823fa668__iq_refso_340"/>

## Allowed Values

ON, OFF



<a name="loioa62ceea984f210159d1a91e2823fa668__iq_refso_341"/>

## Default

ON



<a name="loioa62ceea984f210159d1a91e2823fa668__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa62ceea984f210159d1a91e2823fa668__iq_refso_325"/>

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



<a name="loioa62ceea984f210159d1a91e2823fa668__iq_refso_342"/>

## Remarks

When the ANSI\_SUBSTRING option is set to ON, the behavior of the SUBSTRING function corresponds to ANSI/ISO SQL/2003 behavior. A negative or zero start offset is treated as if the string were padded on the left with non-characters, and gives an error if a negative length is provided.

When this option is set to OFF, the behavior of the SUBSTRING function is the same as in earlier versions of data lake Relational Engine: a negative start offset means an offset from the end of the string, and a negative length means the desired substring ends length characters to the left of the starting offset. Using a start offset of 0 is equivalent to a start offset of 1.

Avoid using non-positive start offsets or negative lengths with the SUBSTRING function. Where possible, use the LEFT or RIGHT functions instead.



<a name="loioa62ceea984f210159d1a91e2823fa668__iq_refso_343"/>

## Example

These examples show the difference in the values returned by the SUBSTRING function based on the setting of the ANSI\_SUBSTRING option:

```
SUBSTRING( 'abcdefgh',-2,4 );
	ansi_substring = Off ==> 'gh' 
	// substring starts at second-last character
	ansi_substring = On  ==> 'gh'
	// takes the first 4 characters of 
	// ???abcdefgh and discards all ?;
```

```
SUBSTRING( 'abcdefgh',4,-2 );
	ansi_substring = Off ==> 'cd'
	ansi_substring = On  ==> value -2 out of range 
	for destination;
```

```
SUBSTRING( 'abcdefgh',0,4 );
	ansi_substring = Off ==> 'abcd'
	ansi_substring = On  ==>; 'abcd'
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SUBSTRING Function \[String\] for Data Lake Relational Engine](../050-system-sql-functions/substring-function-string-for-data-lake-relational-engine-a58787e.md "Returns a substring of a string.")

