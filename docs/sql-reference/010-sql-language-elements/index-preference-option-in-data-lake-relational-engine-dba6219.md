<!-- copydba6219b6e0b48d19fd26ff48d8306e6 -->

# INDEX\_PREFERENCE Option in Data Lake Relational Engine

Controls the choice of indexes to use for queries.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="copydba6219b6e0b48d19fd26ff48d8306e6__section_zx3_g24_hrb"/>

## Syntax

```
INDEX_PREFERENCE = <value>
```



<a name="copydba6219b6e0b48d19fd26ff48d8306e6__iq_refso_620"/>

## Allowed Values

The values control the following:

-   \-10 – avoid DTTM indexes
-   \-9 – avoid TIME indexes
-   \-8 – avoid DATE indexes
-   \-6 – avoid WD indexes
-   \-5 – avoid the default index
-   \-4 – avoid CMP indexes
-   \-2 – avoid HG indexes
-   0 – \(default\) let the optimizer choose
-   2 – prefer HG indexes
-   4 – prefer CMP indexes
-   5 – prefer the default index
-   6 – prefer WD indexes
-   8 – prefer DATE indexes
-   9 – prefer TIME indexes
-   10 – prefer DTTM indexes



<a name="copydba6219b6e0b48d19fd26ff48d8306e6__iq_refso_621"/>

## Default

0



<a name="copydba6219b6e0b48d19fd26ff48d8306e6__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="copydba6219b6e0b48d19fd26ff48d8306e6__iq_refso_622"/>

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



<a name="copydba6219b6e0b48d19fd26ff48d8306e6__iq_refso_623"/>

## Remarks

The data lake Relational Engine optimizer normally chooses the best index available to process local WHERE clause predicates and other operations that can be done within an IQ index. INDEX\_PREFERENCE is used to override the optimizer choice for testing purposes; under most circumstances, it should not be changed.

**Related Information**  


[Set a Database Option](../090-database-options/set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

