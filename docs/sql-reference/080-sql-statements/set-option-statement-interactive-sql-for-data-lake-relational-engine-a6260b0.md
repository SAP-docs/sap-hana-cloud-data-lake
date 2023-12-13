<!-- loioa6260b0f84f21015a64f8842c769c30f -->

# SET OPTION Statement \[Interactive SQL\] for Data Lake Relational Engine

Changes Interactive SQL \(`dbisql`\) options.



<a name="loioa6260b0f84f21015a64f8842c769c30f__section_ovp_dvr_znb"/>

## Usage

This data lake Relational Engine SQL statement can be used when connected as follows:

-   Connected directly to data lake Relational Engine as a data lake Relational Engine user.




<dl>
<dt><b>

Syntax 1

</b></dt>
<dd>

```
SET [ TEMPORARY ] OPTION
   … [ { <userid> | PUBLIC }.]<option-name> = [ <option-value> ];
```



</dd><dt><b>

Syntax 2

</b></dt>
<dd>

```
SET PERMANENT;
```



</dd><dt><b>

Syntax 3

</b></dt>
<dd>

```
SET;
```



</dd>
</dl>



> ### Note:  
> Sections in this topic are minimized. To expand or recollapse a section, click the title next to the right arrow \(*\>*\).



<a name="loioa6260b0f84f21015a64f8842c769c30f__IQ_Usage"/>

## Remarks

Syntax 2 \(`SET PERMANENT`\) stores all current `dbisql` options in the `SYSOPTION` system table. These settings are automatically established every time `dbisql` is started for the current user ID.

Syntax 3 \(`SET`\) shows all current option settings. If there are temporary options set for `dbisql` or the database server, these are shown; otherwise, permanent option settings are shown.

If you enter the name of an option incorrectly when you are setting the option, the incorrect name is saved in the `SYSOPTION` table. You can remove the incorrectly entered name from the `SYSOPTION` table by setting the option PUBLIC with an equality after the option name and no value:

```
SET OPTION PUBLIC.a_mistyped_name=;
```



<a name="loioa6260b0f84f21015a64f8842c769c30f__IQ_Permissions"/>

## Privileges

> ### Note:  
> Some options are only settable by the infrastructure.

-   No specific system privilege is required to set your own options.
-   The SET ANY CUSTOMER PUBLIC OPTION system privilege is required to set database options for another user.
-   The SET ANY CUSTOMER SYSTEM OPTION system privilege is required to set a SYSTEM option for the PUBLIC user ID.
-   The SET ANY CUSTOMER SECURITY OPTION system privilege is required to set a SECURITY option for the PUBLIC user ID.

See [GRANT System Privilege Statement for Data Lake Relational Engine](grant-system-privilege-statement-for-data-lake-relational-engine-a3dfcb0.md) for assistance with granting privileges.

**Related Information**  


[REVOKE System Privilege Statement for Data Lake Relational Engine](revoke-system-privilege-statement-for-data-lake-relational-engine-a3eadda.md "Removes specific system privileges from specific users and the right to administer the privilege.")

[Database Options in Data Lake Relational Engine](../090-database-options/database-options-in-data-lake-relational-engine-a629349.md "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine instance behaves or performs.")

