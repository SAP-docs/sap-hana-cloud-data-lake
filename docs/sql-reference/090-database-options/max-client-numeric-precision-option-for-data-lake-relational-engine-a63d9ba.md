<!-- loioa63d9ba884f21015bfd5986a27e438fb -->

# MAX\_CLIENT\_NUMERIC\_PRECISION Option for Data Lake Relational Engine

Controls the maximum precision for numeric data sent to the client.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa63d9ba884f21015bfd5986a27e438fb__section_zx3_g24_hrb"/>

## Syntax

```
MAX_CLIENT_NUMERIC_PRECISION = <value>
```



<a name="loioa63d9ba884f21015bfd5986a27e438fb__iq_refso_714"/>

## Allowed Values

0 to 126



<a name="loioa63d9ba884f21015bfd5986a27e438fb__iq_refso_715"/>

## Default

0



<a name="loioa63d9ba884f21015bfd5986a27e438fb__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa63d9ba884f21015bfd5986a27e438fb__iq_refso_716"/>

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



<a name="loioa63d9ba884f21015bfd5986a27e438fb__iq_refso_717"/>

## Remarks

When data lake Relational Engine performs its calculation, it promotes data types to an appropriate size that ensures accuracy. The promoted data type might be larger in size than Open Client and some ODBC applications can handle correctly.

When MAX\_CLIENT\_NUMERIC\_PRECISION is a nonzero value, data lake Relational Engine checks that numeric result columns do not exceed this value. If the result column is bigger than MAX\_CUBE\_RESULT allows, and data lake Relational Engine cannot cast it to the specified precision, the query returns this error:

```
Data Exception - data type conversion is not possible %1
SQLCODE = -1001006
```

> ### Note:  
> In SAP SQL Anywhere, the maximum value supported for the numeric function is 255. If the precision of the numeric function exceeds the maximum value supported, you see the error:
> 
> ```
> The result datatype for function '_funcname' exceeds the maximum 
> supported numeric precision of 255. Please set the proper value for precision
>  in numeric function, 'location'
> ```

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[MAX\_CLIENT\_NUMERIC\_SCALE Option for Data Lake Relational Engine](max-client-numeric-scale-option-for-data-lake-relational-engine-a63dca6.md "Controls the maximum scale for numeric data sent to the client.")

[PRECISION Option for Data Lake Relational Engine](precision-option-for-data-lake-relational-engine-a648b25.md "Specifies the maximum number of digits in the result of any decimal arithmetic, for queries on the catalog store only.")

