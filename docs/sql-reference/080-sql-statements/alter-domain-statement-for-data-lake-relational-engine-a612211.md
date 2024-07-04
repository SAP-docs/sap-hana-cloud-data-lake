<!-- loioa612211384f21015886fc13f57b0def2 -->

# ALTER DOMAIN Statement for Data Lake Relational Engine

Renames a user-defined domain or data type.



<a name="loioa612211384f21015886fc13f57b0def2__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.



```
ALTER { DOMAIN | DATATYPE } <user-type>
   RENAME <new-name>
```



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



## Parameters


<dl>
<dt><b>

*<user-type\>*

</b></dt>
<dd>

Specifies the user-defined data type of the domain being renamed.



</dd><dt><b>

RENAME *<new-name\>*

</b></dt>
<dd>

Specifies an identifier representing the new domain name.



</dd>
</dl>



## Remarks

The `ALTER DOMAIN` statement updates the name of the user-defined domain or data type in the `SYSUSERTYPE` system table.

Re-create any procedures, views or events that reference the user-defined domain or data type, so they do not continue to reference the former name.



## Privileges

If you are the database user who created the domain no further privileges are required. If you are not the creator, you require one of the following privileges:

-   ALTER DATATYPE system privilege
-   ALTER ANY OBJECT system privilege

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges. 



## Side Effects

Automatic commit



## Examples

The following example renames the `Address` domain to `MailingAddress`:

```
ALTER DOMAIN Address RENAME MailingAddress;
```

**Related Information**  


[CREATE DOMAIN Statement for Data Lake Relational Engine](create-domain-statement-for-data-lake-relational-engine-a616d8e.md "Creates a user-defined data type in the database.")

[DROP DOMAIN Statement for Data Lake Relational Engine](drop-domain-statement-for-data-lake-relational-engine-b9516c8.md "Removes a domain (data type) from the database.")

[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

