<!-- loioa27d00e384f210158811cdeec5401d23 -->

# ROUND\_TO\_EVEN Option for Data Lake Relational Engine

Controls behavior of the SQL function ROUND when querying data lake Relational Engine tables.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_syntax1"/>

## Syntax

```
ROUND_TO_EVEN = { ON | OFF }
```



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_values1"/>

## Allowed Values

ON, OFF



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_default1"/>

## Default

OFF



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_priv1"/>

## Privileges

Privilege Category: SYSTEM



### 

Requires the SET ANY CUSTOMER SYSTEM OPTION system privilege to set this database option.



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_scope1"/>

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

Yes



</td>
<td valign="top">

No



</td>
<td valign="top">

No



</td>
</tr>
</table>



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_remarks1"/>

## Remarks

The ROUND function rounds the digits after the decimal to the nearest value using the specified number of places. When the value of the last digit of the specified number of places is 5 \(exactly half way between the two nearest values\), the ROUND\_TO\_EVEN option determines how the digit is rounded. When set to ON, the digit rounds to the nearest even number. When set to OFF, the digit rounds to the value with the largest absolute value.



<a name="loioa27d00e384f210158811cdeec5401d23__round_to_even_examples1"/>

## Examples

Table MyTable contains DOUBLE\(10,2\) values:


<table>
<tr>
<th valign="top">

c1



</th>
</tr>
<tr>
<td valign="top">

\-0.35



</td>
</tr>
<tr>
<td valign="top">

\-0.25



</td>
</tr>
<tr>
<td valign="top">

0.25



</td>
</tr>
<tr>
<td valign="top">

0.35



</td>
</tr>
</table>

Execute:

```
select c1, round(c1, 1) from MyTable order by c1;
```

When ROUND\_TO\_EVEN is OFF, the query returns:


<table>
<tr>
<th valign="top">

c1



</th>
<th valign="top">

round\(MyTable,c1,1\)



</th>
</tr>
<tr>
<td valign="top">

\-0.35



</td>
<td valign="top">

\-0.4



</td>
</tr>
<tr>
<td valign="top">

\-0.25



</td>
<td valign="top">

\-0.3



</td>
</tr>
<tr>
<td valign="top">

0.25



</td>
<td valign="top">

0.3



</td>
</tr>
<tr>
<td valign="top">

0.35



</td>
<td valign="top">

0.4



</td>
</tr>
</table>

When ROUND\_TO\_EVEN is ON, the query returns:


<table>
<tr>
<th valign="top">

c1



</th>
<th valign="top">

round\(MyTable,c1,1\)



</th>
</tr>
<tr>
<td valign="top">

\-0.35



</td>
<td valign="top">

\-0.4



</td>
</tr>
<tr>
<td valign="top">

\-0.25



</td>
<td valign="top">

\-0.2



</td>
</tr>
<tr>
<td valign="top">

0.25



</td>
<td valign="top">

0.2



</td>
</tr>
<tr>
<td valign="top">

0.35



</td>
<td valign="top">

0.4



</td>
</tr>
</table>

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[ROUND_TO_EVEN Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/a9bc41c21e7a44b39e48a3bed69742e5.html "Controls behavior of the SQL function ROUND when querying data lake Relational Engine tables.") :arrow_upper_right:

