<!-- loioa655148384f210158440eac57f6bf73f -->

# SORT\_COLLATION Option for Data Lake Relational Engine

Allows implicit use of the SORTKEY function on ORDER BY expressions.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa655148384f210158440eac57f6bf73f__section_zx3_g24_hrb"/>

## Syntax

```
SORT_COLLATION = <value>
```



<a name="loioa655148384f210158440eac57f6bf73f__iq_refso_937"/>

## Allowed Values

Internal, collation\_name, or collation\_id



<a name="loioa655148384f210158440eac57f6bf73f__iq_refso_938"/>

## Default

Internal



<a name="loioa655148384f210158440eac57f6bf73f__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa655148384f210158440eac57f6bf73f__iq_refso_939"/>

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



<a name="loioa655148384f210158440eac57f6bf73f__iq_refso_940"/>

## Remarks

When the value of SORT\_COLLATION is Internal, the ORDER BY clause remains unchanged.

When the value of this option is set to a valid collation name or collation ID, any string expression in the ORDER BY clause is treated as if the SORTKEY function has been invoked.



<a name="loioa655148384f210158440eac57f6bf73f__iq_refso_941"/>

## Example

Set the sort collation to binary:

```
SET TEMPORARY OPTION sort_collation='binary';
```

Setting the sort collation to binary transforms these queries:

```
SELECT Name, ID
FROM Products
ORDER BY Name, ID;
SELECT Name, ID
FROM Products
ORDER BY 1, 2;
```

The queries are transformed into the following:

```
SELECT Name, ID
FROM Products
ORDER BY SORTKEY(Name, 'binary'), ID;
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[SORTKEY Function \[String\] for Data Lake Relational Engine](../050-system-sql-functions/sortkey-function-string-for-data-lake-relational-engine-a5805dd.md "Generates values that can be used to sort character strings based on alternate collation rules.")

