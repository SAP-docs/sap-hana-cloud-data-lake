<!-- loioee9f6aaf17ec413dad8bd2c998adbf54 -->

# TEMP\_EXTRACT\_GZ\_COMPRESSION\_LEVEL Option for Data Lake Relational Engine

The compression level balances compression with speed when the TEMP\_EXTRACT\_COMPRESS option is set to ON.



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__section_k44_ksr_znb"/>

## Usage

This data lake Relational Engine database option can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__section_zx3_g24_hrb"/>

## Syntax

```
TEMP_EXTRACT_GZ_COMPRESSION_LEVEL = <value>;
```



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__iq_refso_992"/>

## Allowed Values

1 to 9



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__iq_refso_993"/>

## Default

6



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__section_k3c_gxb_3qb"/>

## Privileges

Privilege Category: PUBLIC

Requires the SET ANY CUSTOMER PUBLIC OPTION system privilege to set this database option.



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__iq_refso_994"/>

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



<a name="loioee9f6aaf17ec413dad8bd2c998adbf54__iq_refso_995"/>

## Remarks

A value of 1 results in the best speed, while a value of 9 results in the best compression. The default value provides a nice compromise between speed and compression.

This option cannot be used with the TEMP\_EXTRACT\_APPEND, TEMP\_EXTRACT\_SIZE, or TEMP\_EXTRACT\_SIZE*<n\>* options.

In parallel mode, the TEMP\_EXTRACT\_FILE\_EXTENSION option must be set to gz or '' \(empty string\). In serial mode, the TEMP\_EXTRACT\_NAME*<n\>* option must end with .gz.

**Related Information**  


[Set a Database Option](set-a-database-option-0dcb893.md "You set options with the SET OPTION statement.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[GRANT System Privilege Statement for Data Lake Relational Engine](../080-sql-statements/grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md "Grants specific system privileges to users or roles, with or without administrative rights.")

[SET OPTION Statement for Data Lake Relational Engine](../080-sql-statements/set-option-statement-for-data-lake-relational-engine-a625da7.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[TEMP\_EXTRACT\_COMPRESS Option for Data Lake Relational Engine](temp-extract-compress-option-for-data-lake-relational-engine-aef24bc.md "Writes the output file for exports in gzip format. This results in a significant savings of storagespace when exporting tables.")

