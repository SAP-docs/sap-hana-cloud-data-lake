<!-- loio6ed545d21d7a4c159cabfdd39fcc9c73 -->

# ON\_CHARSET\_CONVERSION\_FAILURE Option for Data Lake Relational Engine \(SAP HANA DB-Managed\)

Controls the action taken, if an error is encountered during character conversion.



> ### Restriction:  
> This data lake Relational Engine \(SAP HANA DB-Managed\) database option can be used when:
> 
> -   Connected to SAP HANA database as a SAP HANA database user, and using the REMOTE\_EXECUTE procedure.
> 
>     -   See [REMOTE\_EXECUTE Usage Examples for Setting Database Options](remote-execute-usage-examples-for-setting-database-options-0023bea.md).



<a name="loio6ed545d21d7a4c159cabfdd39fcc9c73__section_aht_5xs_lrb"/>

## Syntax

```
ON_CHARSET_CONVERSION_FAILURE = { IGNORE | WARNING | ERROR }
```



<a name="loio6ed545d21d7a4c159cabfdd39fcc9c73__section_wwb_vxs_lrb"/>

## Allowed Values

-   IGNORE – errors and warnings do not appear.
-   WARNING – substitutions and illegal characters are reported as warnings. Illegal characters are not translated.
-   ERROR – substitutions and illegal characters are reported as errors.



<a name="loio6ed545d21d7a4c159cabfdd39fcc9c73__section_uyy_vxs_lrb"/>

## Default

IGNORE



<a name="loio6ed545d21d7a4c159cabfdd39fcc9c73__section_lmg_ssb_dxb"/>

## Privileges

Privilege Category: PUBLIC



### 

Requires one of:

-   You are a member of the container administrator role, \(SYSHDL\_*<relational\_container\_name\>*\_ROLE\), for the relational container.
-   EXECUTE permission on the REMOTE\_EXECUTE procedure of the SAP HANA database relational container schema associated with the data lake Relational Engine relational container \(SYSHDL\_*<relational\_container\_name\>*\).



<a name="loio6ed545d21d7a4c159cabfdd39fcc9c73__section_abv_xxs_lrb"/>

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



<a name="loio6ed545d21d7a4c159cabfdd39fcc9c73__section_dyh_yxs_lrb"/>

## Remarks

ON\_CHARSET\_CONVERSION\_FAILURE controls the action taken, if an error is encountered during character conversion.

Single-byte to single-byte converters are not able to report substitutions and illegal characters, and must be set to IGNORE.

**Related Information**  


[SET OPTION Statement for Data Lake Relational Engine \(SAP HANA DB-Managed\)](../030-sql-statements/set-option-statement-for-data-lake-relational-engine-sap-hana-db-managed-84a37a4.md "Changes options that affect the behavior of the database and its compatibility with Transact-SQL. Setting the value of an option can change the behavior for all users or an individual user, in either a temporary or permanent scope.")

[Manage Database Options in Data Lake Relational Engine (SAP HANA DB-Managed)](https://help.sap.com/viewer/9220e7fec0fe4503b5c5a6e21d584e63/2023_1_QRC/en-US/964f12eb2961478b8205f5bfd8ee2ec6.html "Data lake Relational Engine database options are configurable settings that change the way the data lake Relational Engine database behaves or performs.") :arrow_upper_right:

[ON_CHARSET_CONVERSION_FAILURE Option for Data Lake Relational Engine](https://help.sap.com/viewer/19b3964099384f178ad08f2d348232a9/2023_1_QRC/en-US/a645abcb84f21015ab8891ab0425a318.html "Controls the action taken, if an error is encountered during character conversion.") :arrow_upper_right:

