<!-- loioa640929184f210158e33c5702629c299 -->

# MAX\_TEMP\_SPACE\_PER\_CONNECTION Option for Data Lake Relational Engine

Limits temporary store space used per connection.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa640929184f210158e33c5702629c299__MAX_TEMP_SPACE_PER_CONN_syntax1"/>

## Syntax

```
MAX_TEMP_SPACE_PER_CONNECTION = <value>
```



<a name="loioa640929184f210158e33c5702629c299__MAX_TEMP_SPACE_PER_CONN_values1"/>

## Allowed Values

Integer \(number of MB\)



<a name="loioa640929184f210158e33c5702629c299__MAX_TEMP_SPACE_PER_CONN_default1"/>

## Default

0 \(no limit on temporary store usage\)



<a name="loioa640929184f210158e33c5702629c299__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa640929184f210158e33c5702629c299__MAX_TEMP_SPACE_PER_CONN_scope1"/>

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



<a name="loioa640929184f210158e33c5702629c299__MAX_TEMP_SPACE_PER_CONN_remarks1"/>

## Remarks

By controlling space per connection, this option enables DBAs to manage the space for both loads and queries. If the connection exceeds the run time quota specified by `MAX_TEMP_SPACE_PER_CONNECTION`, data lake Relational Engine rolls back the current statement and returns this message to the IQ message file or client user:

```
The current operation has been canceled: Max_Temp_Space_Per_Connection exceeded
```

Conditions that may fill the buffer cache include read or write errors, lack of main or temp space, or being out of memory. Data lake Relational Engine may return the first error encountered in these situations and the DBA must determine the appropriate solution.



<a name="loioa640929184f210158e33c5702629c299__MAX_TEMP_SPACE_PER_CONN_examples1"/>

## Examples



### Example 1

Set a 500 GB limit for all connections:

```
SET OPTION 
PUBLIC.MAX_TEMP_SPACE_PER_CONNECTION = 512000
```



### Example 2

Set a 10 TB limit for all connections:

```
SET OPTION 
PUBLIC.MAX_TEMP_SPACE_PER_CONNECTION = 10485760
```



### Example 3

Set a 5000 MB limit for user `wilson`:

```
SET OPTION 
wilson.MAX_TEMP_SPACE_PER_CONNECTION = 5000
```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[QUERY\_TEMP\_SPACE\_LIMIT Option for Data Lake Relational Engine](query-temp-space-limit-option-for-data-lake-relational-engine-a650c63.md "Specifies the maximum estimated amount of temp space before a query is rejected.")

[MAX_TEMP_SPACE_PER_CONNECTION Option for Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/a898e08b84f21015969fa437e89860c8/2023_2_QRC/en-US/713e6c2a4c594b22ae18a449e8ecd9dc.html "Limits temporary store space used per connection.") :arrow_upper_right:

