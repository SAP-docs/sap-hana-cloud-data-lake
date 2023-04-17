<!-- loioa874375084f21015bab3df18885053fc -->

# FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine

Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.



> ### Restriction:  
> This data lake Relational Engine database option can be used when connected as follows:
> 
> -   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



## Syntax

```
FP_NBIT_IQ15_COMPATIBILITY = { ON | OFF }
```



## Allowed Values

ON, OFF



## Default

OFF



<a name="loioa874375084f21015bab3df18885053fc__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



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



## Remarks

The FP\_NBIT\_IQ15\_COMPATIBILITY option provides tokenized FP support. All newly created and modified tokenized FP indexes in will be NBit.

The FP\_NBIT\_IQ15\_COMPATIBILITY ON/OFF setting only pertains to tokenized FP creation and cut-off behavior:

If FP\_NBIT\_IQ15\_COMPATIBILITY='ON', the database engine:

-   Enables the MINIMIZE\_STORAGE, FP\_LOOKUP\_SIZE, FP\_LOOKUP\_SIZE\_PPM options.
-   Creates DATE data types as NBit FP, even if IQ UNIQUE\(0\) is specified.
-   Rolls over to Flat FP at the 3 byte FP cutoff \(16,777,216 distinct\).
-   Can tokenize data widths up to 255.

If FP\_NBIT\_IQ15\_COMPATIBILITY is set to OFF:

-   MINIMIZE\_STORAGE, FP\_LOOKUP\_SIZE, FP\_LOOKUP\_SIZE\_PPM options are ignored.
-   DATE data types are not automatically NBit.
-   Data widths up to 32767 may be tokenized.
-   NBit FP \(tokenized\) upper bound limit is NBit 31 \(2,147,483,648 distinct values\).
-   NBit sizing options determine rollover behavior:
    -   IQ UNIQUE\(0\) loads a column as Flat FP
    -   Columns without IQ UNIQUE load as NBit up to the auto-size limits
    -   Columns where IQ UNIQUE\(*<n\>*\) is less than the auto-size limit load as NBit


**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[FP\_NBIT\_AUTOSIZE\_LIMIT Option for Data Lake Relational Engine](fp-nbit-autosize-limit-option-for-data-lake-relational-engine-a873755.md "Limits the number of distinct values in columns that implicitly load as NBit FP.")

[FP\_NBIT\_ENFORCE\_LIMITS Option for Data Lake Relational Engine](fp-nbit-enforce-limits-option-for-data-lake-relational-engine-a874045.md "Enforces sizing limits for explicit and implicit NBit columns.")

[FP\_NBIT\_LOOKUP\_MB Option for Data Lake Relational Engine](fp-nbit-lookup-mb-option-for-data-lake-relational-engine-a873a52.md "Limits the total dictionary size per column for implicit NBit FP columns.")

[FP\_NBIT\_ROLLOVER\_MAX\_MB Option for Data Lake Relational Engine](fp-nbit-rollover-max-mb-option-for-data-lake-relational-engine-a873d4b.md "Sets a threshold for the total dictionary size for implicit NBit rollovers to Flat FP.")

[FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine](fp-lookup-size-optionfor-data-lake-relational-engine-a63673f.md "Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.")

[FP\_LOOKUP\_SIZE\_PPM Option for Data Lake Relational Engine](fp-lookup-size-ppm-option-for-data-lake-relational-engine-a636a3a.md "Controls the amount of main buffer cache allocated to FP indexes in data lake Relational Engine 15databases.")

[MINIMIZE\_STORAGE Option for Data Lake Relational Engine](minimize-storage-option-for-data-lake-relational-engine-a64115e.md "Minimizes use of storagespace for newly created columns in data lake Relational Engine databases.")

