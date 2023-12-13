<!-- loioa64115e484f210158eea9e1d74b5a7ed -->

# MINIMIZE\_STORAGE Option for Data Lake Relational Engine

Minimizes use of storagespace for newly created columns in data lake Relational Engine databases.



<a name="loioa64115e484f210158eea9e1d74b5a7ed__section_d3p_24q_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioa64115e484f210158eea9e1d74b5a7ed__section_qhm_yvs_lrb"/>

## Syntax

```
MINIMIZE_STORAGE = { ON | OFF };
```



<a name="loioa64115e484f210158eea9e1d74b5a7ed__iq_refso_771"/>

## Allowed Values

ON, OFF



<a name="loioa64115e484f210158eea9e1d74b5a7ed__iq_refso_772"/>

## Default

OFF



<a name="loioa64115e484f210158eea9e1d74b5a7ed__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioa64115e484f210158eea9e1d74b5a7ed__iq_refso_773"/>

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



<a name="loioa64115e484f210158eea9e1d74b5a7ed__iq_refso_549"/>

## Dependencies

MINIMIZE\_STORAGE applies to databases running with FP\_NBIT\_IQ15\_COMPATIBILITY is set to ON. If it is set to OFF, the database engine ignores this option.



<a name="loioa64115e484f210158eea9e1d74b5a7ed__iq_refso_774"/>

## Remarks

If FP\_NBIT\_IQ15\_COMPATIBILITY is ON, MINIMIZE\_STORAGE optimizes storage for new columns by using as little as one byte of space per row wherever appropriate. By default, this option is OFF for the PUBLIC role, and the specialized storage optimization does not occur for all newly created columns; when MINIMIZE\_STORAGE is OFF for the PUBLIC role but ON as a temporary user option, one-byte storage is used for new columns created by that user ID.

In data lake Relational Engine databases, setting MINIMIZE\_STORAGE is ON is equivalent to placing an IQ UNIQUE 255 clause on every new column, with the exception of certain data types that are by nature too wide for one-byte storage. When MINIMIZE\_STORAGE is ON, there is no need to specify IQ UNIQUE, except for columns with more than 65536 unique values.

When the ratio of main memory to the number of columns is large, turning MINIMIZE\_STORAGE to ON is beneficial. Otherwise, storage of new columns generally benefits by turning this option OFF.

> ### Note:  
> Avoid running a database when FP\_NBIT\_IQ15\_COMPATIBILITY is set to ON. All data lake Relational Engine runtime behavior is available with the data lake Relational Engine interface.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[FP\_LOOKUP\_SIZE Optionfor Data Lake Relational Engine](fp-lookup-size-optionfor-data-lake-relational-engine-a63673f.md "Specifies the number of lookup pages and cache memory allocated for Lookup FP indexes in data lake Relational Engine databases.")

[INDEX\_ADVISOR Option for Data Lake Relational Engine](index-advisor-option-for-data-lake-relational-engine-a63943d.md "Generates messages suggesting additional column indexes that may improve performance of one or more queries.")

[FP\_LOOKUP\_SIZE\_PPM Option for Data Lake Relational Engine](fp-lookup-size-ppm-option-for-data-lake-relational-engine-a636a3a.md "Controls the amount of main buffer cache allocated to FP indexes in data lake Relational Engine 15databases.")

[FP\_NBIT\_IQ15\_COMPATIBILITY Option for Data Lake Relational Engine](fp-nbit-iq15-compatibility-option-for-data-lake-relational-engine-a874375.md "Provides support for tokenized FP indexes similar to that available in data lake Relational Engine.")

